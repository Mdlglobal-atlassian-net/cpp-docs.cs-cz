---
title: CMFCAcceleratorKeyAssignCtrl – třída
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
ms.openlocfilehash: 5e57bf149fdbc293692c613afcabcf2d11d32221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505472"
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl – třída

Třída rozšiřuje třídu CEdit pro podporu dalších systémových tlačítek, jako je například ALT, Control a Shift. [](../../mfc/reference/cedit-class.md) `CMFCAcceleratorKeyAssignCtrl`

## <a name="syntax"></a>Syntaxe

```
class CMFCAcceleratorKeyAssignCtrl : public CEdit
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|`CMFCAcceleratorKeyAssignCtrl` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|Načte strukturu pro stisknutou klávesovou zkratku `CMFCAcceleratorKeyAssignCtrl` v objektu. `ACCEL`|
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|Určuje, zda byla definována klávesová zkratka.|
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|Používá se třídou [CWinApp](../../mfc/reference/cwinapp-class.md) k překladu zpráv oken před odesláním do funkcí Windows [TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage) a [DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage) . (Potlačení [CWnd::P retranslatemessage](../../mfc/reference/cwnd-class.md#pretranslatemessage).)|
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|Resetuje klávesovou zkratku.|

## <a name="remarks"></a>Poznámky

Tato třída rozšiřuje funkčnost `CEdit` třídy podporou klávesových zkratek, označovaných také jako akcelerátory kláves. Třída funguje jako [Třída CEdit](../../mfc/reference/cedit-class.md) a může také rozpoznat systémová tlačítka. `CMFCAcceleratorKeyAssignCtrl`

Tato třída mapuje kombinace fyzických klávesových zkratek na řetězcové hodnoty. Předpokládejme například, že kombinace kláves ALT + B je namapována na řetězec "ALT + B". Když uživatel stiskne tuto kombinaci kláves v `CMFCAcceleratorKeyAssignCtrl` objektu, zobrazí se uživateli klávesa ALT + B. Další informace o mapování mezi klávesovými klávesami a formátem řetězce naleznete v tématu [Třída CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit `CMFCAcceleratorKeyAssignCtrl` objekt a použít jeho `ResetKey` metodu k resetování klávesových zkratek.

[!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CMFCAcceleratorKeyAssignCtrl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxacceleratorkeyassignctrl. h

##  <a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl

Vytvoří objekt [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) .

```
CMFCAcceleratorKeyAssignCtrl();
```

##  <a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel

Načte strukturu pro klávesovou zkratku stisknutou v objektu [CMFCAcceleratorKeyAssignCtrl.](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) `ACCEL`

```
ACCEL const* GetAccel() const;
```

### <a name="return-value"></a>Návratová hodnota

`ACCEL` Struktura, která popisuje klávesovou zkratku.

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze načíst `ACCEL` strukturu pro klávesovou zkratku, kterou uživatel zadal `CMFCAcceleratorKeyAssignCtrl` do objektu.

##  <a name="isfocused"></a>  CMFCAcceleratorKeyAssignCtrl::IsFocused

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

```
BOOL IsFocused() const;
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="iskeydefined"></a>  CMFCAcceleratorKeyAssignCtrl::IsKeyDefined

Určuje, zda byla v objektu [CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) definována klávesová zkratka.

```
BOOL IsKeyDefined() const;
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud uživatel již stiskl platnou kombinaci klíčů, která definuje klávesovou zkratku; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Pomocí této funkce lze určit, zda uživatel zadal platnou klávesovou zkratku v `CMFCAcceleratorKeyAssignCtrl` objektu. Pokud klávesová zkratka existuje, můžete použít metodu [CMFCAcceleratorKeyAssignCtrl:: GetAccel](#getaccel) k získání `ACCEL` struktury přidružené k této klávesové zkratce.

##  <a name="pretranslatemessage"></a>  CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage

Další podrobnosti najdete ve zdrojovém kódu ve složce **VC\\atlmfc\\src\\MFC** v instalaci sady Visual Studio.

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>Parametry

pro *pMsg*<br/>

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

##  <a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey

Resetuje klávesovou zkratku.

```
void ResetKey();
```

### <a name="remarks"></a>Poznámky

Funkce vymaže text ovládacího prvku pro úpravy. To zahrnuje všechny klávesové zkratky, které uživatel stiskne.

## <a name="see-also"></a>Viz také:

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CMFCAcceleratorKey – třída](../../mfc/reference/cmfcacceleratorkey-class.md)
