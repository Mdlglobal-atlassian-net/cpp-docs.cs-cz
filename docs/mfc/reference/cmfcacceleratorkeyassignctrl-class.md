---
title: Třída CMFCAcceleratorKeyAssignCtrl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7728df79bf2ab842910b580b1404f109034e55b7
ms.sourcegitcommit: f1b051abb1de3fe96350be0563aaf4e960da13c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37037243"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl – třída
`CMFCAcceleratorKeyAssignCtrl` Třída rozšiřuje [CEdit třída](../../mfc/reference/cedit-class.md) pro podporu tlačítka další systémové například ALT, řízení a SHIFT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Vytvoří `CMFCAcceleratorKeyAssignCtrl` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Načte `ACCEL` struktury pro stisknuto klávesovou zkratku `CMFCAcceleratorKeyAssignCtrl` objektu.|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Určuje, zda byla definována klávesovou zkratku.|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Používá třída [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit zprávy oken, než jsou odeslány do [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) a [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) funkce systému Windows. (Přepisuje [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Obnoví klávesovou zkratku.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída rozšiřuje funkce `CEdit` třída díky podpoře klávesové zkratky, také známé jako klávesy akcelerátoru. `CMFCAcceleratorKeyAssignCtrl` Třídy funkce jako [CEdit třída](../../mfc/reference/cedit-class.md) a taky poznáte tlačítka systému.  
  
 Tato třída mapuje kombinace fyzické klávesových zkratek řetězcové hodnoty. Předpokládejme například, kombinace kláves ALT + B je namapována na řetězec "Alt + B". Když uživatel stiskne tuto kombinaci kláves v `CMFCAcceleratorKeyAssignCtrl` objektů, zobrazí se uživateli "Alt + B". Další informace o mapování mezi klávesové zkratky a formát řetězce najdete v tématu [CMFCAcceleratorKey třída](../../mfc/reference/cmfcacceleratorkey-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCAcceleratorKeyAssignCtrl` objektu a použít jeho `ResetKey` metoda resetovat klávesovou zkratku.  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CMFCAcceleratorKeyAssignCtrl`   
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxacceleratorkeyassignctrl.h  
  
##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl  
 Vytvoří [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objektu.  
  
```  
CMFCAcceleratorKeyAssignCtrl();
```  
  
##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel  
 Načte `ACCEL` struktury pro stisknuto klávesovou zkratku [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objektu.  
  
```  
ACCEL const* GetAccel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `ACCEL` Struktura, která popisuje klávesovou zkratku.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete získat `ACCEL` strukturu pro klávesovou zkratku, která uživatel zadal do vaší `CMFCAcceleratorKeyAssignCtrl` objektu.  
  
##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined  
 Určuje, zda byla definována klávesovou zkratku v [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objektu.  
  
```  
BOOL IsKeyDefined() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud uživatel již má stisknutí platnou kombinaci klíče, které definují klávesovou zkratku; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k určení, zda uživatel zadal platný klávesovou zkratku ve vaší `CMFCAcceleratorKeyAssignCtrl` objektu. Pokud existuje klávesovou zkratku, můžete použít [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) metoda získat `ACCEL` struktura přidružené k této klávesové zkratky.  
  
##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 [v] *pMsg*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey  
 Obnoví klávesovou zkratku.  
  
```  
void ResetKey();
```  
  
### <a name="remarks"></a>Poznámky  
 Funkce vymaže text ovládací prvek upravit. To zahrnuje všechny klávesové zkratky, které uživatel klepl na tlačítko.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey – třída](../../mfc/reference/cmfcacceleratorkey-class.md)
