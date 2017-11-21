---
title: "Třída CKeyFrame | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
dev_langs: C++
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 69ec01c3ad488dc9236369719fcd5060ba75e13d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ckeyframe-class"></a>CKeyFrame – třída
Představuje klíčový snímek animace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CKeyFrame : public CBaseKeyFrame;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CKeyFrame::CKeyFrame](#ckeyframe)|Přetíženo. Vytvoří klíčový snímek, který závisí na jiné klíčový snímek.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|Přidá klíčový scénáře. (Přepisuje [CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard).)|  
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|Přidá klíčový do scénáře po přechodu.|  
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|Přidá klíčový do scénáře na posunu.|  
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|Vrátí ukazatel klíčový snímek, který tento klíčový snímek závisí na.|  
|[CKeyFrame::GetOffset](#getoffset)|Vrátí posun od jiných klíčový snímek.|  
|[CKeyFrame::GetTransition](#gettransition)|Vrací ukazatel na tento klíčový snímek závisí na přechod.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CKeyFrame::m_offset](#m_offset)|Určuje posun tento klíčový snímek z klíčový uložené v m_pExistingKeyFrame.|  
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|Ukládá ukazatele na existující keframe. Klíčový tento snímek se přidá do scénáře s m_offset do existujícího klíčového snímku.|  
|[CKeyFrame::m_pTransition](#m_ptransition)|Ukládá do transtion, který začíná na tento klíčový ukazatel.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída implementuje klíčový snímek animace. Klíčový představuje časového okamžiku v rámci scénáře a slouží k určení počáteční a koncový čas přechody. Klíčový může být založeno na jiné klíčový snímek a mít posun (v sekundách) z něj, nebo může být založeno na přechod a představují časového okamžiku při ukončení tento přechod.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)  
  
 [CKeyFrame](../../mfc/reference/ckeyframe-class.md)  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxanimationcontroller.h  
  
##  <a name="addtostoryboard"></a>CKeyFrame::AddToStoryboard  
 Přidá klíčový scénáře.  
  
```  
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na scénář.  
  
 `bDeepAdd`  
 Určuje, jestli chcete přidat klíčový snímek nebo přechod rekurzivně.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud klíčový snímek byl úspěšně přidán.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda přidá klíčový do scénáře. Pokud je závislý na jiných klíčový snímek nebo přechod a bDeepAdd má hodnotu TRUE, tato metoda se pokusí přidat je rekurzivní.  
  
##  <a name="addtostoryboardaftertransition"></a>CKeyFrame::AddToStoryboardAfterTransition  
 Přidá klíčový do scénáře po přechodu.  
  
```  
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na scénář.  
  
 `bDeepAdd`  
 Určuje, zda chcete přidat rekurzivně přechodu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud klíčový snímek byl úspěšně přidán.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána rámcem přidat klíčový do scénáře po přechodu.  
  
##  <a name="addtostoryboardatoffset"></a>CKeyFrame::AddToStoryboardAtOffset  
 Přidá klíčový do scénáře na posunu.  
  
```  
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,  
    BOOL bDeepAdd);
```  
  
### <a name="parameters"></a>Parametry  
 `pStoryboard`  
 Ukazatel na scénář.  
  
 `bDeepAdd`  
 Určuje, zda chcete-li přidat klíčový tento klíčový snímek závisí na rekurzivní.  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota TRUE, pokud klíčový snímek byl úspěšně přidán.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána rámcem přidat klíčový do scénáře na posunu.  
  
##  <a name="ckeyframe"></a>CKeyFrame::CKeyFrame  
 Vytvoří klíčový snímek, který závisí na přechod.  
  
```  
CKeyFrame(CBaseTransition* pTransition);

 
CKeyFrame(
    CBaseKeyFrame* pKeyframe,  
    UI_ANIMATION_SECONDS offset = 0.0);
```  
  
### <a name="parameters"></a>Parametry  
 `pTransition`  
 Ukazatel na přechod.  
  
 `pKeyframe`  
 Ukazatel na klíčový snímek.  
  
 `offset`  
 Posun v sekundách, z určeného pKeyframe klíčový snímek.  
  
### <a name="remarks"></a>Poznámky  
 Sestavené klíčový snímek bude reprezentovat časového okamžiku v rámci scénáře při ukončení zadaný přechodu.  
  
##  <a name="getexistingkeyframe"></a>CKeyFrame::GetExistingKeyframe  
 Vrátí ukazatel klíčový snímek, který tento klíčový snímek závisí na.  
  
```  
CBaseKeyFrame* GetExistingKeyframe();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel na klíčový snímek, nebo hodnota NULL, pokud tento klíčový snímek není závislá na jiných klíčový snímek.  
  
### <a name="remarks"></a>Poznámky  
 Toto je přistupující objekt pro tento klíčový snímek závisí na klíčový snímek.  
  
##  <a name="getoffset"></a>CKeyFrame::GetOffset  
 Vrátí posun od jiných klíčový snímek.  
  
```  
UI_ANIMATION_SECONDS GetOffset();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Posun v sekundách z jiných klíčový snímek.  
  
### <a name="remarks"></a>Poznámky  
 Tato metoda by měla být volána k určení posun v sekundách z jiných klíčový snímek.  
  
##  <a name="gettransition"></a>CKeyFrame::GetTransition  
 Vrací ukazatel na tento klíčový snímek závisí na přechod.  
  
```  
CBaseTransition* GetTransition();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Neplatný ukazatel na přechod nebo hodnota NULL, pokud tento klíčový snímek nezávisí na přechod.  
  
### <a name="remarks"></a>Poznámky  
 Toto je přistupující objekt pro tento klíčový snímek závisí na přechod.  
  
##  <a name="m_offset"></a>CKeyFrame::m_offset  
 Určuje posun tento klíčový snímek z klíčový uložené v m_pExistingKeyFrame.  
  
```  
UI_ANIMATION_SECONDS m_offset;  
```  
  
##  <a name="m_pexistingkeyframe"></a>CKeyFrame::m_pExistingKeyFrame  
 Ukládá ukazatele na existující keframe. Klíčový tento snímek se přidá do scénáře s m_offset do existujícího klíčového snímku.  
  
```  
CBaseKeyFrame* m_pExistingKeyFrame;  
```  
  
##  <a name="m_ptransition"></a>CKeyFrame::m_pTransition  
 Ukládá do transtion, který začíná na tento klíčový ukazatel.  
  
```  
CBaseTransition* m_pTransition;  
```  
  
## <a name="see-also"></a>Viz také  
 [Třídy](../../mfc/reference/mfc-classes.md)
