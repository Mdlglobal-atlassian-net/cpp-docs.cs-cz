---
title: Třída CBaseKeyFrame | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::CBaseKeyFrame
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::GetAnimationKeyframe
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::IsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_bIsKeyframeAtOffset
- AFXANIMATIONCONTROLLER/CBaseKeyFrame::m_keyframe
dev_langs:
- C++
helpviewer_keywords:
- CBaseKeyFrame [MFC], CBaseKeyFrame
- CBaseKeyFrame [MFC], AddToStoryboard
- CBaseKeyFrame [MFC], GetAnimationKeyframe
- CBaseKeyFrame [MFC], IsAdded
- CBaseKeyFrame [MFC], IsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_bAdded
- CBaseKeyFrame [MFC], m_bIsKeyframeAtOffset
- CBaseKeyFrame [MFC], m_keyframe
ms.assetid: 285a2eff-e7c4-43be-b5aa-737727e6866d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2f538874b1690be920e9c7a3b3f494ca6851c532
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cbasekeyframe-class"></a>CBaseKeyFrame – třída
Implementuje základních funkcí klíčový snímek.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CBaseKeyFrame : public CObject;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CBaseKeyFrame::CBaseKeyFrame](#cbasekeyframe)|Vytvoří objekt klíčový snímek.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CBaseKeyFrame::AddToStoryboard](#addtostoryboard)|Přidá klíčový do scénáře.|  
|[CBaseKeyFrame::GetAnimationKeyframe](#getanimationkeyframe)|Vrátí základní hodnotu klíčový snímek.|  
|[CBaseKeyFrame::IsAdded](#isadded)|Určuje, zda je klíčový přidala do scénáře.|  
|[CBaseKeyFrame::IsKeyframeAtOffset](#iskeyframeatoffset)|Určuje, zda klíčový snímek, který má být přidán do scénáře na posunu nebo po přechodu.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CBaseKeyFrame::m_bAdded](#m_badded)|Určuje, zda tento klíčový snímek byl přidán do scénáře.|  
|[CBaseKeyFrame::m_bIsKeyframeAtOffset](#m_biskeyframeatoffset)|Určuje, zda tento klíčový snímek přidaly do scénáře v posun z jiné existující klíčový snímek, nebo na konci některé přechodu.|  
|[CBaseKeyFrame::m_keyframe](#m_keyframe)|Představuje klíčový rozhraní API systému Windows animace. Když není inicializován klíčový je nastavena na předdefinované hodnotu UI_ANIMATION_KEYFRAME_STORYBOARD_START.|  
  
## <a name="remarks"></a>Poznámky  
 Zapouzdří UI_ANIMATION_KEYFRAME proměnné. Slouží jako základní třída pro žádnou implementaci klíčový snímek. Klíčový představuje časového okamžiku v rámci scénáře a slouží k určení počáteční a koncový čas přechody. Existují dva typy klíčových snímků - klíčové snímky přidány do scénáře na zadaném posunu (v čase) nebo přidat po zadaný přechod klíčových snímků. Vzhledem k tomu, že před spuštěním animace nemůže být známé dobami trvání některé přechody, skutečné hodnoty některých klíčových snímků jsou určeny pouze za běhu. Protože klíčových snímků může záviset na přechody, které mohou záviset na klíčových snímků, je důležité, aby se zabránilo nekonečná rekurze, které jsou při vytváření řetězů @keyframe, které určuje.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CBaseKeyFrame`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>  CBaseKeyFrame::AddToStoryboard  
 Přidá klíčový do scénáře.  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na scénář.  
  
 `bDeepAdd`  
 Pokud tento parametr je TRUE a klíčový snímek, který chcete přidat, závisí na některé @keyframe, které určuje nebo přechod, tato metoda se pokusí přidat tento klíčový snímek nebo přechod do první scénáře.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud klíčový snímek byl přidán do scénáře úspěšně; jinak hodnota FALSE.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda je volána k přidat klíčový do scénáře.  
  
##  <a name="cbasekeyframe"></a>  CBaseKeyFrame::CBaseKeyFrame  
 Vytvoří objekt klíčový snímek.  
  
```  
CBaseKeyFrame();
```  
  
##  <a name="getanimationkeyframe"></a>  CBaseKeyFrame::GetAnimationKeyframe  
 Vrátí základní hodnotu klíčový snímek.  
  
```  
UI_ANIMATION_KEYFRAME GetAnimationKeyframe() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Klíčový aktuální. Výchozí hodnota je UI_ANIMATION_KEYFRAME_STORYBOARD_START.  
  
### <a name="remarks"></a>Poznámky  
 Toto je základní hodnotu @keyframe, které určuje přistupující objekt.  
  
##  <a name="isadded"></a>  CBaseKeyFrame::IsAdded  
 Určuje, zda je klíčový přidala do scénáře.  
  
```  
BOOL IsAdded() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud klíčový se přidá do scénáře; otehrwise hodnotu FALSE.  
  
### <a name="remarks"></a>Poznámky  
 V základní třídě IsAdded vždy vrátí hodnotu TRUE, ale je přepsání v odvozené třídy.  
  
##  <a name="iskeyframeatoffset"></a>  CBaseKeyFrame::IsKeyframeAtOffset  
 Určuje, zda klíčový snímek, který má být přidán do scénáře na posunu nebo po přechodu.  
  
```  
BOOL IsKeyframeAtOffset() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud klíčový snímek, který má být přidán do scénáře na některé zadaný posunu. FALSE, pokud klíčový snímek, který má být přidán do scénáře po některé přechodu.  
  
### <a name="remarks"></a>Poznámky  
 Určuje, zda klíčový snímek, který má být přidán do scénáře na posunu. Odvozené třídy musí být zadán posun nebo přechod.  
  
##  <a name="m_badded"></a>  CBaseKeyFrame::m_bAdded  
 Určuje, zda tento klíčový snímek byl přidán do scénáře.  
  
```  
BOOL m_bAdded;  
```  
  
##  <a name="m_biskeyframeatoffset"></a>  CBaseKeyFrame::m_bIsKeyframeAtOffset  
 Určuje, zda tento klíčový snímek přidaly do scénáře v posun z jiné existující klíčový snímek, nebo na konci některé přechodu.  
  
```  
BOOL m_bIsKeyframeAtOffset;  
```  
  
##  <a name="m_keyframe"></a>  CBaseKeyFrame::m_keyframe  
 Představuje klíčový rozhraní API systému Windows animace. Když není inicializován klíčový je nastavena na předdefinované hodnotu UI_ANIMATION_KEYFRAME_STORYBOARD_START.  
  
```  
UI_ANIMATION_KEYFRAME m_keyframe;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
