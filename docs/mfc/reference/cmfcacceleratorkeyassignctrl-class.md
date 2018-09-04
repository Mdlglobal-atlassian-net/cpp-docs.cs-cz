---
title: Cmfcacceleratorkeyassignctrl – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 6adb289759e2050a67f9284e2763c44461c38c0d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43683525"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Cmfcacceleratorkeyassignctrl – třída
`CMFCAcceleratorKeyAssignCtrl` Třída rozšiřuje [cedit – třída](../../mfc/reference/cedit-class.md) k podpoře dalších systémových tlačítek, jako například ALT, SHIFT a CONTROL.  
  
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
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Načte `ACCEL` strukturu pro stisknuto klávesovou zkratku `CMFCAcceleratorKeyAssignCtrl` objektu.|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Určuje, zda byla definována klávesovou zkratku.|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Používá třída [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit okno zprávy před odesláním do [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage) funkce Windows. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Obnoví klávesovou zkratku.|  
  
## <a name="remarks"></a>Poznámky  
 Tato třída rozšiřuje funkce `CEdit` třídy díky podpoře klávesové zkratky, označované také jako přístupové klávesy. `CMFCAcceleratorKeyAssignCtrl` Funkcí jako třídy [cedit – třída](../../mfc/reference/cedit-class.md) a také poznáte systémových tlačítek.  
  
 Tato třída mapuje fyzické klávesových zkratek řetězcové hodnoty. Předpokládejme například, kombinace kláves ALT + B je namapován na řetězec "Alt + B". Když uživatel stiskne tuto kombinaci kláves v `CMFCAcceleratorKeyAssignCtrl` objektu, zobrazí se uživateli "Alt + B". Další informace o mapování klávesových zkratek a formát řetězce najdete v tématu [cmfcacceleratorkey – třída](../../mfc/reference/cmfcacceleratorkey-class.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit `CMFCAcceleratorKeyAssignCtrl` objektu a použít jeho `ResetKey` metoda resetovat klávesovou zkratku.  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [Třídy CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [Cedit –](../../mfc/reference/cedit-class.md)  
  
 `CMFCAcceleratorKeyAssignCtrl`   
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxacceleratorkeyassignctrl.h  
  
##  <a name="cmfcacceleratorkeyassignctrl"></a>  CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl  
 Vytvoří [cmfcacceleratorkeyassignctrl –](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objektu.  
  
```  
CMFCAcceleratorKeyAssignCtrl();
```  
  
##  <a name="getaccel"></a>  CMFCAcceleratorKeyAssignCtrl::GetAccel  
 Načte `ACCEL` strukturu pro stisknuto klávesovou zkratku [cmfcacceleratorkeyassignctrl –](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objektu.  
  
```  
ACCEL const* GetAccel() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 `ACCEL` Struktura, která popisuje klávesovou zkratku.  
  
### <a name="remarks"></a>Poznámky  
 Pomocí této funkce můžete načíst `ACCEL` strukturu pro klávesovou zkratku, která uživatel zadal do vaší `CMFCAcceleratorKeyAssignCtrl` objektu.  
  
##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused  
 Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.  
  
```  
BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined  
 Určuje, zda byla definována klávesovou zkratku v [cmfcacceleratorkeyassignctrl –](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) objektu.  
  
```  
BOOL IsKeyDefined() const;  
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové, pokud uživatel stiskne již platnou kombinaci kláves, které definují klávesovou zkratku; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce slouží k určení, zda uživatel zadal platný klávesovou zkratku v vaše `CMFCAcceleratorKeyAssignCtrl` objektu. Pokud existuje klávesovou zkratku můžete použít [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) metodu k získání `ACCEL` struktura přidružené k této klávesovou zkratku.  
  
##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage  
 Další podrobnosti najdete ve zdrojovém kódu v **VC\\atlmfc\\src\\mfc** složce instalace sady Visual Studio.  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 [in] *pMsg*  
  
### <a name="return-value"></a>Návratová hodnota  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="resetkey"></a>  CMFCAcceleratorKeyAssignCtrl::ResetKey  
 Obnoví klávesovou zkratku.  
  
```  
void ResetKey();
```  
  
### <a name="remarks"></a>Poznámky  
 Funkce vymaže úpravy textu ovládacího prvku. To zahrnuje všechny klávesové zkratky, které uživatel stiskl.  
  
## <a name="see-also"></a>Viz také  
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [Třídy](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey – třída](../../mfc/reference/cmfcacceleratorkey-class.md)
