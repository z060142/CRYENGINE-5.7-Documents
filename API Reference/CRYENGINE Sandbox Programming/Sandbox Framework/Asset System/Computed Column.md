# Computed Column

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/35258993
- Page ID: 35258993
- Breadcrumb: CRYENGINE Sandbox Programming > Sandbox Framework > Asset System > Computed Column
- Parent: Asset System

## Content

## Overview

It is possible to add a computed column to the Asset Browser detail view.

```
static CItemModelAttribute filesCountAttribute("Files count", eAttributeType_Int, CItemModelAttribute::StartHidden);

CAssetManager* const pAssetManager = GetIEditor()->GetAssetManager();
pAssetManager->GetAssetModel()->AddComputedColumn(&filesCountAttribute, [](const CAsset* pAsset, const CItemModelAttribute* pAttribute, int role)
{
if (role == Qt::DisplayRole && pAsset)
{
return QVariant(pAsset->GetFilesCount());
}
return QVariant();
});
```

Once added the column is fully functional as an ordinary column. For example assets can be ordered or/and filtered by the column values.

![Image](https://www.cryengine.com/docs/static/attachments/35395350)

## Table of Contents
