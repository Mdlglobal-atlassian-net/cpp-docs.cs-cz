---
title: Třída CMFCAcceleratorKeyAssignCtrl
ms.date: 10/18/2018
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
ms.openlocfilehash: 2021a2069885c6314859a65d528cf03712c524b6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751732"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>Třída CMFCAcceleratorKeyAssignCtrl

Třída `CMFCAcceleratorKeyAssignCtrl` rozšiřuje [třídu CEdit](../../mfc/reference/cedit-class.md) tak, aby podporovala další systémová tlačítka, jako jsou ALT, CONTROL a SHIFT.

## <a name="syntax"></a>Syntaxe

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|Vytvoří `CMFCAcceleratorKeyAssignCtrl` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Načte `ACCEL` strukturu klávesové zkratky `CMFCAcceleratorKeyAssignCtrl` stisknuté v objektu.|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Určuje, zda byla definována klávesová zkratka.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Používá třídy [CWinApp](../../mfc/reference/cwinapp-class.md) přeložit okno zprávy před jejich odesláním do [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) Windows funkce. (Přepíše [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCAcceleratorKeyAssignCtrl::Resetkey](#resetkey)|Obnoví klávesovou zkratku.|

## <a name="remarks"></a>Poznámky

Tato třída rozšiřuje funkce `CEdit` třídy podporou klávesových zkratek, označovaných také jako klávesové zkratky. Třída `CMFCAcceleratorKeyAssignCtrl` funguje jako [třída CEdit](../../mfc/reference/cedit-class.md) a dokáže také rozpoznat systémová tlačítka.

Tato třída mapuje kombinace fyzických klávesových zkratek na řetězcové hodnoty. Předpokládejme například, že kombinace kláves ALT + B je mapována na řetězec "Alt + B". Když uživatel stiskne tuto `CMFCAcceleratorKeyAssignCtrl` kombinaci kláves v objektu, "Alt + B" se zobrazí uživateli. Další informace o mapování mezi klávesovými zkratkami a formátem řetězce naleznete v [tématu CMFCAcceleratorKey Class](../../mfc/reference/cmfcacceleratorkey-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCAcceleratorKeyAssignCtrl` vytvořit objekt `ResetKey` a použít jeho metodu k obnovení klávesové zkratky.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CEditovat](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxacceleratorkeyassignctrl.h

## <a name="cmfcacceleratorkeyassignctrlcmfcacceleratorkeyassignctrl"></a><a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Vytvoří objekt [CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
CMFCAcceleratorKeyAssignCtrl();
```

## <a name="cmfcacceleratorkeyassignctrlgetaccel"></a><a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel

Načte `ACCEL` strukturu klávesové zkratky stisknuté v objektu [CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Návratová hodnota

Struktura, `ACCEL` která popisuje klávesovou zkratku.

### <a name="remarks"></a>Poznámky

Pomocí této funkce `ACCEL` můžete načíst strukturu pro klávesovou `CMFCAcceleratorKeyAssignCtrl` zkratku, kterou uživatel zadal do objektu.

## <a name="cmfcacceleratorkeyassignctrlisfocused"></a><a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcacceleratorkeyassignctrliskeydefined"></a><a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Určuje, zda byla v objektu [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) definována klávesová zkratka.

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud uživatel již stiskl platnou kombinaci kláves, které definují klávesovou zkratku; jinak 0.

### <a name="remarks"></a>Poznámky

Tato funkce slouží k určení, zda uživatel `CMFCAcceleratorKeyAssignCtrl` zadal do objektu platnou klávesovou zkratku. Pokud klávesová zkratka existuje, můžete použít [CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel) metodu `ACCEL` k získání struktury přidružené k této klávesové zkratce.

## <a name="cmfcacceleratorkeyassignctrlpretranslatemessage"></a><a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Další podrobnosti naleznete ve zdrojovém kódu umístěném ve složce **MFC\\knihovny\\VC src\\** instalace sady Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

[v] *pMsg*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

## <a name="cmfcacceleratorkeyassignctrlresetkey"></a><a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::Resetkey

Obnoví klávesovou zkratku.

```cpp
void ResetKey();
```

### <a name="remarks"></a>Poznámky

Funkce vymaže text ovládacího prvku pro úpravy. To zahrnuje všechny klávesové zkratky, které uživatel stiskl.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey – třída](../../mfc/reference/cmfcacceleratorkey-class.md)
