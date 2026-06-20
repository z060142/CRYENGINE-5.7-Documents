# How to Create a Simple Flying Entity

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756813/pages/23306470
- Page ID: 23306470
- Breadcrumb: CRYENGINE Engine Code > Engine Modules > CryAISystem > Obsolete AI Documentation > How to Create a Simple Flying Entity
- Parent: Obsolete AI Documentation

## Content

##
Overview

Let's call our sample flying entity Flyer. We will need the following files:

-
`
Game/Scripts/Entities/AI/Flyer.lua
`

-
`
Game/Scripts/Entities/AI/Flyer_x.lua
`

-
`
Game/Scripts/AI/SelectionTrees/Flyer.xml
`

-
`
Game/Scripts/AI/Behaviors/Personalities/Flyer/FlyerIdle.lua
`

-
`
Code/Game/GameDll/Flyer.h
`

-
`
Code/Game/GameDll/Flyer.cpp
`

-
`
Code/Game/GameDll/FlyerMovementController.h
`

-
`
Code/Game/GameDll/FlyerMovementController.cpp
`
Additionally, we will need to add the following line to the related section of
`
Code/Game/GameDll/GameFactory.cpp
`
:

```

`
REGISTER_FACTORY(pFramework, "Flyer", CFlyer, true /* is AI */);
`

```

It is necessary make the new entity appear in the list of AI entities in the Editor (
**
RollupBar -> Objects -> Entity -> AI -> Flyer
**
).

##
Individual Files

##
Game/Scripts/Entities/AI/Flyer.lua

```

`
Script.ReloadScript("Scripts/Entities/AI/Flyer_x.lua");

CreateActor(Flyer_x);
Flyer = CreateAI(Flyer_x)
Flyer:Expose();

`

```

##
Game/Scripts/Entities/AI/Flyer_x.lua

```

`
Script.ReloadScript("SCRIPTS/Entities/actor/BasicActor.lua");
Script.ReloadScript("SCRIPTS/Entities/AI/Shared/BasicAI.lua");

Flyer_x =
{
   AnimationGraph = "",

   AIType = AIOBJECT_2D_FLY,

   PropertiesInstance =
   {
      aibehavior_behaviour = "FlyerIdle",
   },

   Properties =
   {
      esBehaviorSelectionTree = "Flyer",

      fileModel = "Objects/Characters/Dragon/Dragon.cdf",

      Damage =
      {
         health = 1,
      },
   },

   gameParams =
   {
      stance =
      {
         {
            stanceId = STANCE_STAND,
            normalSpeed = 10,
            maxSpeed = 20,
            heightCollider = 0,
            heightPivot = -1,
            size = { x = 3, y = 3, z = 3 },
            viewOffset = { x = 0, y = 0, z = 0 },
            name = "fly",
         },
      },
   },

   AIMovementAbility =
   {
      b3DMove = 1,
      optimalFlightHeight = 15,
      minFlightHeight = 10,
      maxFlightHeight = 30,
      pathType = AIPATH_HELI,
   },
}

function Flyer_x:OnResetCustom()
   self.AI.bUpdate = nil;
end

`

```

Naturally, you may need an animation graph and your own character model, rather than Dragon.cdf. Tables gameParams.stance and gameParams.AIMovementAbility will then need to be updated accordingly.

Health was set to 1 for debugging reasons (debugging character death).

In this example, we want to control the update rate (2.5 Hz in our example) and that why we will later need self.AI.bUpdate.

##
Game/Scripts/AI/SelectionTrees/Flyer.xml

```

`
<SelectionTrees>
   <SelectionTree name="Flyer" type="BehaviorSelectionTree">
      <Leaf name="FlyerIdle"/>
   </SelectionTree>
</SelectionTrees>

`

```

##
Game/Scripts/AI/Behaviors/Personalities/Flyer/FlyerIdle.lua

```

`
local fMinUpdateTime = 0.4;

FlyerIdleBehavior = CreateAIBehavior("FlyerIdle",
{
   --------------------------------------------------------------------------
   Constructor = function(self, entity)
      entity.AI.vZero = { x = 0, y = 0, z = 0 };
      AI.SetForcedNavigation(entity.id, entity.AI.vZero);

      entity.AI.vUp = { x = 0, y = 0, z = 1 };

      entity.AI.vLastEnemyPos = {};
      entity.AI.vTargetPos = {};

      AI.CreateGoalPipe("Flyer_LookAtAttTarget");
      AI.PushGoal("Flyer_LookAtAttTarget", "locate",  0, "atttarget");
      AI.PushGoal("Flyer_LookAtAttTarget", "+lookat", 0, 0, 0, true, 1);
      AI.PushGoal("Flyer_LookAtAttTarget", "timeout", 1, 60);

      AI.CreateGoalPipe("Flyer_LookAtRefPoint");
      AI.PushGoal("Flyer_LookAtRefPoint", "locate",  0, "refpoint");
      AI.PushGoal("Flyer_LookAtRefPoint", "+lookat", 0, 0, 0, true, 1);
      AI.PushGoal("Flyer_LookAtRefPoint", "timeout", 1, 60);

      entity.AI.state = 1;
      self:PATROL_START(entity);

      entity.AI.bUpdate = true;
      Script.SetTimerForFunction(fMinUpdateTime * 1000, "FlyerIdleBehavior.UPDATE", entity);
   end,

   --------------------------------------------------------------------------
   OnEnemyHeard = function(self, entity, distance)
      self:PATROL_START(entity);
   end,

   --------------------------------------------------------------------------
   OnEnemySeen = function(self, entity, distance)
      self:PATROL_START(entity);
   end,

   --------------------------------------------------------------------------
   OnNoTarget = function(self, entity)
      self:PATROL_START(entity);
   end,

   --------------------------------------------------------------------------
   UPDATE = function(entity)
      if (not entity.id) then
         return;
      end

      local myEntity = System.GetEntity(entity.id);
      if (not myEntity) then
         return;
      end

      if ((entity.AI == nil) or (not entity.AI.bUpdate) or (entity:GetSpeed() == nil) or (not entity:IsActive())) then
         local vZero = { x = 0, y = 0, z = 0 };
         AI.SetForcedNavigation(myEntity.id, vZero);
         return;
      end

      entity.AI.bUpdate = true;
      Script.SetTimerForFunction(fMinUpdateTime * 1000, "FlyerIdleBehavior.UPDATE", entity);

      FlyerIdleBehavior:PATROL(entity);
   end,

   --------------------------------------------------------------------------
   -- Fly around entity.AI.vLastEnemyPos, 15 meters away
   --------------------------------------------------------------------------
   PATROL_START = function(self, entity)
      local attTarget = AI.GetAttentionTargetEntity(entity.id);
      if (attTarget) then
         CopyVector(entity.AI.vLastEnemyPos, attTarget:GetPos());
      else
         CopyVector(entity.AI.vLastEnemyPos, entity:GetPos());
      end

      -- Calculate "from me to target" 2D vector (length = 15)
      local vTmp = {};
      CopyVector(vTmp, entity.AI.vLastEnemyPos);
      SubVectors(vTmp, vTmp, entity:GetPos());
      if (LengthSqVector(vTmp) < 1) then
         CopyVector(vTmp, entity:GetDirectionVector(1));
      end
      vTmp.z = 0;
      NormalizeVector(vTmp);
      if (entity.AI.state == 1) then
         FastScaleVector(vTmp, vTmp, 15);
      else
         FastScaleVector(vTmp, vTmp, -15);
      end

      -- Fly past the enemy
      FastSumVectors(entity.AI.vTargetPos, vTmp, entity.AI.vLastEnemyPos);

      entity.AI.stateEntryTime = System.GetCurrTime();

      entity:SelectPipe(0, "do_nothing");
      if (attTarget) then
         entity:SelectPipe(0, "Flyer_LookAtAttTarget");
      else
         -- Descrease my height by 3 meters
         CopyVector(vTmp, entity:GetPos());
         vTmp.x = entity.AI.vTargetPos.x;
         vTmp.y = entity.AI.vTargetPos.y;
         vTmp.z = vTmp.z - 3;
         AI.SetRefPointPosition(entity.id, vTmp);
         entity:SelectPipe(0, "Flyer_LookAtRefPoint");
      end
   end,

   --------------------------------------------------------------------------
   PATROL = function(self, entity)
      -- Calculate "from target to me" 2D vector (length = 15)
      local dir15 = {};
      local pos = {};
      CopyVector(pos, entity:GetPos());
      SubVectors(dir15, pos, entity.AI.vTargetPos);
      if (LengthSqVector(dir15) < 1) then
         CopyVector(dir15, entity:GetDirectionVector(1));
      end
      dir15.z = 0;
      NormalizeVector(dir15);
      FastScaleVector(dir15, dir15, 15);

      -- Rotate the "from target to me" 2D vector by 10 degrees
      local vForcedNav = {};
      local actionAngle = 10 * 3.1416 / 180;
      RotateVectorAroundR(vForcedNav, dir15, entity.AI.vUp, actionAngle * fMinUpdateTime * -1);

      -- Go to the end of the rotated vector
      FastSumVectors(vForcedNav, vForcedNav, entity.AI.vTargetPos);
      SubVectors(vForcedNav, vForcedNav, pos);
      vForcedNav.z = 0;
      NormalizeVector(vForcedNav);
      FastScaleVector(vForcedNav, vForcedNav, 5);

      -- Fly 15-30 meters about the target
      if (pos.z > entity.AI.vLastEnemyPos.z + 30) then
         vForcedNav.z = -5;
      end
      if (pos.z < entity.AI.vLastEnemyPos.z + 15) then
         vForcedNav.z = 3;
      end

      self:AvoidObstacles(entity, vForcedNav);

      AI.SetForcedNavigation(entity.id, vForcedNav);

      if (System.GetCurrTime() - entity.AI.stateEntryTime > 20) then
         entity.AI.state = 3 - entity.AI.state;
         self:PATROL_START(entity);
      end
   end,

   --------------------------------------------------------------------------
   AvoidObstacles = function(self, entity, vForcedNav)
      -- Calculate prospective velocity
      local vel = {};
      entity:GetVelocity(vel);
      FastSumVectors(vel, vel, vForcedNav);

      local vPeak = {};
      local pos = {};
      CopyVector(pos, entity:GetPos());
      CopyVector(vPeak, AI.IsFlightSpaceVoidByRadius(pos, vel, 2.5));   -- Here, Flight Navigation data are used

      if (LengthVector(vPeak) < 0.001) then
         return;
      end

      -- Fly over peaks

      if (vPeak.z > pos.z) then
         if (vPeak.z - pos.z < 100.0) then
            vForcedNav.x = (vPeak.x - pos.x) * 0.5;
            vForcedNav.y = (vPeak.y - pos.y) * 0.5;
            vForcedNav.z = 0;

            local length2d = LengthVector(vForcedNav);
            if (length2d > 16) then
               length2d = 16
            end
            NormalizeVector(vForcedNav);
            FastScaleVector(vForcedNav, vForcedNav, length2d);
            vForcedNav.z = (vPeak.z - pos.z) * 3.5;
         end
      end

      if (vPeak.z < pos.z) then
         if ((pos.z - vPeak.z) < 5) then
            vForcedNav.z = 5 - (pos.z - vPeak.z);
         else
            vForcedNav.z = 0;
         end
      end

      vForcedNav.z = clamp(vForcedNav.z, -30, 30);
   end,
})

`

```

The Flyer basically flies around some point on a map. If it detects the player, it starts to fly around him or her.

AI.SetForcedNavigation sets velocity of the entity.

##
Code/Game/GameDll/Flyer.h

```

`
#ifndef __FLYER_H__
#define __FLYER_H__

#if _MSC_VER > 1000
#pragma once
#endif

#include "Player.h"

class CFlyer : public CPlayer
{
public:

   struct SMovementRequestParams
   {
      Vec3 vLookTargetPos;
      Vec3 vMoveDir;
      float fDesiredSpeed;

      explicit SMovementRequestParams(CMovementRequest& movementRequest) :
         vLookTargetPos(movementRequest.HasLookTarget() ? movementRequest.GetLookTarget() : Vec3Constants<float>::fVec3_Zero),
         vMoveDir(ZERO),
         fDesiredSpeed(movementRequest.HasDesiredSpeed() ? movementRequest.GetDesiredSpeed() : 1.f)
      {
      }
   };

   struct SBodyInfo
   {
      Vec3 vEyePos;
      Vec3 velocity;
      EStance eStance;
      const SStanceInfo* pStanceInfo;

      SBodyInfo() :
         vEyePos(ZERO),
         velocity(ZERO),
         eStance(STANCE_NULL),
         pStanceInfo(NULL)
      {
      }
   };

   CFlyer();

   virtual void GetMemoryUsage(ICrySizer* pCrySizer) const { pCrySizer->Add(*this); }
   virtual void FullSerialize(TSerialize ser);
   virtual void PrePhysicsUpdate();
   virtual void Revive(bool bFromInit = false);

   void GetActorInfo(SBodyInfo& bodyInfo);
   void SetActorMovement(SMovementRequestParams& movementRequestParam);

protected:

   virtual IActorMovementController* CreateMovementController();

private:

   void ProcessMovement(float frameTime);   // Ad-hoc

   void SetDesiredVelocity(const Vec3& vDesiredVelocity);
   void SetDesiredDirection(const Vec3& vDesiredDir);

   Vec3 m_vDesiredVelocity;
   Quat m_qDesiredRotation;

   SCharacterMoveRequest m_moveRequest;
};

#endif   // #ifndef __FLYER_H__

`

```

In this example entity, we have very rudimentary inputs (only movement requests) and state (only body info).

##
Code/Game/GameDll/Flyer.cpp

```

`
#include "StdAfx.h"
#include "Flyer.h"
#include "FlyerMovementController.h"
#include "GameUtils.h"

CFlyer::CFlyer() :
   m_vDesiredVelocity(ZERO),
   m_qDesiredRotation(IDENTITY)
{
   memset(&m_moveRequest.prediction, 0, sizeof(m_moveRequest.prediction));
}

void CFlyer::FullSerialize(TSerialize ser)
{
   CPlayer::FullSerialize(ser);

   ser.BeginGroup("CFlyer");
   ser.Value("vDesiredVelocity", m_vDesiredVelocity);
   ser.Value("qDesiredRotation", m_qDesiredRotation);
   ser.EndGroup();
}

void CFlyer::PrePhysicsUpdate()
{
   if (m_stats.isRagDoll)
      return;

   if (GetHealth() <= 0.f)
      return;

   IEntity* pEntity = GetEntity();
   if (pEntity->IsHidden())
      return;

   if (IPhysicalEntity* pPhysicalEntity = pEntity->GetPhysics())
   {
      pe_player_dynamics player_dynamics;
      player_dynamics.gravity.zero();
      pPhysicalEntity->SetParams(&player_dynamics);
   }

   float frameTime = gEnv->pTimer->GetFrameTime();

   if (m_pMovementController)
   {
      SActorFrameMovementParams params;
      m_pMovementController->Update(frameTime, params);
   }

   if (m_linkStats.CanMove() && m_linkStats.CanRotate())
   {
      ProcessMovement(frameTime);

      if (m_pAnimatedCharacter)
      {
         m_pAnimatedCharacter->AddMovement(m_moveRequest);
      }
   }
}

void CFlyer::Revive(bool bFromInit)
{
   CPlayer::Revive(bFromInit);

   SetDesiredVelocity(Vec3Constants<float>::fVec3_Zero);
   SetDesiredDirection(GetEntity()->GetWorldTM().GetColumn1());
}

void CFlyer::GetActorInfo(SBodyInfo& bodyInfo)
{
   IEntity* pEntity = GetEntity();

   bodyInfo.vEyePos = pEntity->GetSlotWorldTM(0) * m_eyeOffset;
   bodyInfo.velocity = m_velocity;
   bodyInfo.eStance = m_stance;
   bodyInfo.pStanceInfo = GetStanceInfo(m_stance);
}

void CFlyer::SetActorMovement(SMovementRequestParams& movementRequestParams)
{
   SMovementState state;
   GetMovementController()->GetMovementState(state);

   if (movementRequestParams.vMoveDir.IsZero())
   {
      Vec3 vDesiredDirection = movementRequestParams.vLookTargetPos.IsZero()
         ? GetEntity()->GetWorldRotation() * FORWARD_DIRECTION
         : (movementRequestParams.vLookTargetPos - state.eyePosition).GetNormalizedSafe();
      SetDesiredDirection(vDesiredDirection);
      SetDesiredVelocity(Vec3Constants<float>::fVec3_Zero);
   }
   else
   {
      Vec3 vDesiredDirection = movementRequestParams.vLookTargetPos.IsZero()
         ? movementRequestParams.vMoveDir.GetNormalizedSafe()
         : (movementRequestParams.vLookTargetPos - state.eyePosition).GetNormalizedSafe();
      SetDesiredDirection(vDesiredDirection);
      SetDesiredVelocity(movementRequestParams.vMoveDir * movementRequestParams.fDesiredSpeed);
   }
}

IActorMovementController* CFlyer::CreateMovementController()
{
   return new CFlyerMovementController(this);
}

// Ad-hoc
void CFlyer::ProcessMovement(float frameTime)
{
   frameTime = min(1.f, frameTime);

   float desiredSpeed = m_vDesiredVelocity.GetLength();
   const float maxDeltaSpeed = 100.f;

   float deltaSpeed = min(maxDeltaSpeed, fabsf(desiredSpeed - m_stats.speed));

   // Advance "m_velocity" towards "m_vDesiredVelocity" at the speed proportional to (1 / square(deltaSpeed))
   Interpolate(
      m_velocity,
      m_vDesiredVelocity,
      2.5f * ((deltaSpeed > 0.f) ? min(frameTime, 2.f / square(deltaSpeed)) : frameTime),
      1.f);

   Quat desiredVelocityQuat = m_qDesiredRotation;

   // pitch/roll
   if (desiredSpeed > 0.f && m_stats.speed > 0.f)
   {
      const Vec3& vUp = Vec3Constants<float>::fVec3_OneZ;
      Vec3 vForward = m_velocity.GetNormalized();

      // If the direction is not too vertical
      if (fabs(vForward.dot(vUp)) < cosf(DEG2RAD(3.f)))
      {
         vForward.z = 0;
         vForward.NormalizeSafe();
         Vec3 vRight = vForward.Cross(vUp);
         vRight.NormalizeSafe();

         Vec3 vDesiredVelocityNormalized = m_vDesiredVelocity.GetNormalized();

         // Roll in an aircraft-like manner
         float cofRoll = 6.f * vRight.dot(vDesiredVelocityNormalized) * (m_stats.speed / maxDeltaSpeed);
         clamp(cofRoll, -1.f, 1.f);
         desiredVelocityQuat *= Quat::CreateRotationY(DEG2RAD(60.f) * cofRoll);

         float cofPitch = vDesiredVelocityNormalized.dot(vForward) * (deltaSpeed / maxDeltaSpeed);
         clamp(cofPitch, -1.f, 1.f);
         desiredVelocityQuat *= Quat::CreateRotationX(DEG2RAD(-60.f) * cofPitch);
      }
   }

   float cofRot = 2.5f * ((deltaSpeed > 0.f) ? min(frameTime, 1.f / square(deltaSpeed)) : frameTime);
   clamp(cofRot, 0.f, 1.f);
   const Quat& qRotation = GetEntity()->GetRotation();
   Quat newRot = Quat::CreateSlerp(qRotation, desiredVelocityQuat, cofRot);
   m_moveRequest.rotation = qRotation.GetInverted() * newRot;
   m_moveRequest.rotation.Normalize();

   m_moveRequest.velocity = m_velocity;

   m_moveRequest.type = eCMT_Fly;
}

void CFlyer::SetDesiredVelocity(const Vec3& vDesiredVelocity)
{
   m_vDesiredVelocity = vDesiredVelocity;
}

void CFlyer::SetDesiredDirection(const Vec3& vDesiredDirection)
{
   m_qDesiredRotation.SetRotationVDir(vDesiredDirection.GetNormalizedSafe());
}

`

```

Basically, every frame (in CFlyer::PrePhysicsUpdate), the entity asks the movement controller (see next post) for the desired velocity, and also orients the entity (see CFlyer::SetActorMovement) so that it looks our way, but doesn't stare all the time.

##
Code/Game/GameDll/FlyerMovementController.h

```

`
#ifndef __FLYER_MOVEMENT_CONTROLLER_H__
#define __FLYER_MOVEMENT_CONTROLLER_H__

#pragma once

#include "IMovementController.h"
#include "Actor.h"

class CFlyer;

class CFlyerMovementController : public IActorMovementController
{
public:

   CFlyerMovementController(CFlyer* pFlyer) : m_pFlyer(pFlyer) {}

   virtual bool RequestMovement(CMovementRequest& request);
   virtual void GetMovementState(SMovementState& movementState) { movementState = m_movementState; }
   virtual bool GetStanceState(const SStanceStateQuery& query, SStanceState& state) { return false; }
   virtual void Reset() {}
   virtual bool Update(float frameTime, SActorFrameMovementParams& actorFrameMovementParams);
   virtual bool GetStats(SStats& stats) { return false; }
   virtual void PostUpdate(float frameTime) {}
   virtual void Release() { delete this; }
   virtual void Serialize(TSerialize& ser) {}

private:

   CFlyer* m_pFlyer;

   CMovementRequest m_movementRequest;
   SMovementState m_movementState;
};

#endif   // #ifndef __FLYER_MOVEMENT_CONTROLLER_H__

`

```

##
Code/Game/GameDll/FlyerMovementController.cpp

```

`
#include "StdAfx.h"
#include "FlyerMovementController.h"
#include "Flyer.h"

bool CFlyerMovementController::RequestMovement(CMovementRequest& movementRequest)
{
   CFlyer::SMovementRequestParams movementRequestParams(movementRequest);

   if (movementRequest.HasForcedNavigation())
   {
      movementRequestParams.vMoveDir = movementRequest.GetForcedNavigation();
      movementRequestParams.fDesiredSpeed = movementRequestParams.vMoveDir.GetLength();
      movementRequestParams.vMoveDir.NormalizeSafe();
   }

   m_pFlyer->SetActorMovement(movementRequestParams);

   return true;
}

bool CFlyerMovementController::Update(SActorFrameMovementParams&)
{
   IEntity* pEntity = m_pFlyer->GetEntity();

   CFlyer::SBodyInfo bodyInfo;
   m_pFlyer->GetActorInfo(bodyInfo);

   SMovementState& state = m_movementState;
   state.pos = pEntity->GetWorldPos();
   state.entityDirection = pEntity->GetWorldRotation() * Vec3Constants<float>::fVec3_OneY;
   state.animationBodyDirection = state.entityDirection;
   state.upDirection = Vec3Constants<float>::fVec3_OneZ;
   state.weaponPosition.zero();
   state.aimDirection = state.entityDirection;
   state.fireDirection = state.entityDirection;
   state.eyePosition = bodyInfo.vEyePos;
   state.eyeDirection = state.entityDirection;
   state.lean = 0.f;
   state.peekOver = 0.f;
   state.m_StanceSize = bodyInfo.pStanceInfo->GetStanceBounds();
   state.m_ColliderSize = bodyInfo.pStanceInfo->GetColliderBounds();
   state.fireTarget.zero();
   state.stance = bodyInfo.eStance;
   state.animationEyeDirection = state.entityDirection;
   state.movementDirection = state.entityDirection;
   state.lastMovementDirection = state.entityDirection;
   state.desiredSpeed = bodyInfo.velocity.GetLength();
   state.minSpeed = 0.f;
   state.normalSpeed = bodyInfo.pStanceInfo->normalSpeed;
   state.maxSpeed = bodyInfo.pStanceInfo->maxSpeed;
   state.slopeAngle = 0.f;
   state.atMoveTarget = false;
   state.isAlive = (m_pFlyer->GetHealth() > 0.f);
   state.isAiming = false;
   state.isFiring = false;
   state.isVisible = !pEntity->IsInvisible();

   return true;
}

`

```
