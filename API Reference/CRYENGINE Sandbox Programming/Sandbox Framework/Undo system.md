# Undo system

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/26873116
- Page ID: 26873116
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Undo system
- Parent: Sandbox Framework

## Content

### Classes:

**IUndoManager** (Code\Sandbox\EditorInterface\IUndoManager.h) Stores the list of undo commands and provides all operations needed for manipulation with this list. Currently there is only one instance that can be accessed via ** GetIEditor()->GetIUndoManager()**. ** CUndo** (Code\Sandbox\EditorInterface\IUndoObject.h) It's a helper class for easy use of the GetIEditor()->GetIUndoManager() instance. ** IUndoObject** (Code\Sandbox\EditorInterface\IUndoObject.h) Interface you have to implement for individual undo steps.

Please refer the CUndoVariableChange (Code\Sandbox\EditorQt\Controls\PropertyItem.cpp).

1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 | `class` ` CUndoVariableChange:``public` ` IUndoObject` `{` ` public``:` ` CUndoVariableChange(IVariable* var,``const` ` char``* undoDescription)` `{` `// Stores the current state of this object.` ` assert``(var!= 0);` ` m_undoDescription = undoDescription;` ` m_var = var;` ` m_undo = m_var->Clone(``false``);` `}` ` protected``:` ` virtual` ` int` ` GetSize()` `{` ` int` ` size =``sizeof``(*``this``);` `//if (m_var)` `//size += m_var->GetSize();` ` if` `(m_undo)` ` size += m_undo->GetSize();` ` if` `(m_redo)` ` size += m_redo->GetSize();` ` return` ` size;` `}` ` virtual` ` const` ` char``* GetDescription() {``return` ` m_undoDescription; };` ` virtual` ` void` ` Undo(``bool` ` bUndo)` `{` ` if` `(bUndo)` `{` ` m_redo = m_var->Clone(``false``);` `}` ` m_var->CopyValue(m_undo);` `}` ` virtual` ` void` ` Redo()` `{` ` if` `(m_redo)` ` m_var->CopyValue(m_redo);` `}` ` private``:` ` CString m_undoDescription;` ` TSmartPtr<IVariable> m_undo;` ` TSmartPtr<IVariable> m_redo;` ` TSmartPtr<IVariable> m_var;` `};`
--- | ---

**Important:** when you implement your own IUndoObject the function IUndoObject::Undo(bool bUndo) takes boolean argument - every undo object needs to remember its original state and the new state, i.e. in case of implementation of the CUndoVariableChange it has TSmartPtr<IVariable> m_undo and TSmartPtr<IVariable> m_redo variables for storing the old and new state - the m_undo variable is filled by the current m_var data (that is before the m_var is modified) in the constructor of the CUndoVariableChange. The m_redo variable needs to be filled after the value was modified, so it's filled the first time the IUndoObject::Undo(bool bUndo) function is called - when it's first time called the bUndo is true, so now you fill the m_redo variable with the current m_var data (that is after the m_var is modified from outside).

### Usage

To start the undo command recording, you have to first call function IUndoManager::Begin(). To record the undo step you have to call IUndoManager::RecordUndo(pMyCommand). You can call this function multiple times if you want to group more commands together. To finish the recording you have to call IUndoManager::Accept("Desc") or IUndoManager::Cancel() if you want to discard the commands. There is a helper class for all these functions **CUndo** that calls begin/accept/cancel in its constructor/destructor and also provides a function for the recording.

The typical usage looks like this:

1 2 3 4 | `CUndo undo(``"Group Objects"``);` ` if` `(CUndo::IsRecording())` ` CUndo::Record(``new` ` CUndoGroupObjectOpenClose(pPrefabObj));`
--- | ---

**Events:**

When the IUndoManager undo buffer is changed, it emits several events via IUndoManager::signalBufferChanged. See its usage in Code\Sandbox\EditorQt\Undo\CommandHistory.cpp.
