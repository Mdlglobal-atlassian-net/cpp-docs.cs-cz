---
title: "Třída CMenuTearOffManager | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
dev_langs: C++
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
caps.latest.revision: "31"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: efb1b7acc2f4eb779de49559b5b566e89d518a0e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager – třída
Spravuje úplné vypnutí nabídky. Úplné vypnutí nabídky je nabídky v řádku nabídek. Uživatele můžete odebrat z nabídky úplné vypnutí v nabídce panelu způsobuje v nabídce úplné vypnutí float.  
  
   [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
   
## <a name="syntax"></a>Syntaxe  
  
```  
class CMenuTearOffManager : public CObject  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|Vytvoří `CMenuTearOffManager` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMenuTearOffManager::Build](#build)||  
|[CMenuTearOffManager::GetRegPath](#getregpath)||  
|[CMenuTearOffManager::Initialize](#initialize)|Inicializuje `CMenuTearOffManager` objektu.|  
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||  
|[CMenuTearOffManager::Parse](#parse)||  
|[CMenuTearOffManager::Reset](#reset)||  
|[CMenuTearOffManager::SetInUse](#setinuse)||  
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||  
  
## <a name="remarks"></a>Poznámky  
 Chcete-li použít úplné vypnutí nabídky v aplikaci, musíte mít `CMenuTearOffManager` objektu. Ve většině případů nebude vytvořit nebo inicializovat `CMenuTearOffManager` objektu přímo. To se zpracovává za vás při volání [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus) funkce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a inicializace `CMenuTearOffManager` objekt voláním `CWinAppEX::EnableTearOffMenus` metoda. Tento fragment kódu je součástí [ukázkové aplikace Word Pad](../../visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMenuTearOffManager`   
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxmenutearoffmanager.h  
  
##  <a name="build"></a>CMenuTearOffManager::Build  

  
```  
void Build(
    UINT uiTearOffBarID,  
    CString& strText);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiTearOffBarID`  
 [v]`strText`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="cmenutearoffmanager"></a>CMenuTearOffManager::CMenuTearOffManager  
 Vytvoří [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objektu.  
  
```  
CMenuTearOffManager();
```  
  
### <a name="remarks"></a>Poznámky  
 Ve většině případů byste je neměli vytvářet `CMenuTearOffManager` ručně. Vytvoří rozhraní vaší aplikace `CMenuTearOffManager` objektu při volání [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus).  
  
##  <a name="getregpath"></a>CMenuTearOffManager::GetRegPath  

  
```  
LPCTSTR GetRegPath() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="initialize"></a>CMenuTearOffManager::Initialize  
 Inicializuje [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md) objektu.  
  
```  
BOOL Initialize(
    LPCTSTR lpszRegEntry,  
    UINT uiTearOffMenuFirst,  
    UINT uiTearOffMenuLast);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`lpszRegEntry`  
 Řetězec, který obsahuje cestu položky registru. Aplikace ukládá nastavení pro řádky úplné vypnutí v této položky registru.  
  
 [v]`uiTearOffMenuFirst`  
 První nabídky ID nabídky úplné vypnutí.  
  
 [v]`uiTearOffMenuLast`  
 ID poslední nabídky nabídky úplné vypnutí.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Rozsah ID nabídky z `uiTearOffMenuFirst` k `uiTearOffMenuLast` musí být průběžné intervalu. Interval definuje počet úplné vypnutí nabídky, které se mohou objevit v aplikaci najednou.  
  
##  <a name="isdynamicid"></a>CMenuTearOffManager::IsDynamicID  

  
```  
BOOL IsDynamicID(UINT uiID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiID`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="parse"></a>CMenuTearOffManager::Parse  

  
```  
UINT Parse(CString& str);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`str`  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="reset"></a>CMenuTearOffManager::Reset  

  
```  
void Reset(HMENU hmenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hmenu`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setinuse"></a>CMenuTearOffManager::SetInUse  

  
```  
void SetInUse(
    UINT uiCmdId,  
    BOOL bUse = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`uiCmdId`  
 [v]`bUse`  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="setuptearoffmenus"></a>CMenuTearOffManager::SetupTearOffMenus  

  
```  
void SetupTearOffMenus(HMENU hMenu);
```  
  
### <a name="parameters"></a>Parametry  
 [v]`hMenu`  
  
### <a name="remarks"></a>Poznámky  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CWinAppEx – třída](../../mfc/reference/cwinappex-class.md)
