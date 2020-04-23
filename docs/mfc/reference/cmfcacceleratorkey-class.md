---
title: CMFCAcceleratorKey – třída
ms.date: 11/04/2016
f1_keywords:
- CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::CMFCAcceleratorKey
- AFXACCELERATORKEY/CMFCAcceleratorKey::Format
- AFXACCELERATORKEY/CMFCAcceleratorKey::SetAccelerator
helpviewer_keywords:
- CMFCAcceleratorKey [MFC], CMFCAcceleratorKey
- CMFCAcceleratorKey [MFC], Format
- CMFCAcceleratorKey [MFC], SetAccelerator
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
ms.openlocfilehash: a814618d3bda27d5b4ace12209dd93343ef2eef9
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81751775"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey – třída

Pomocná třída, která implementuje mapování a formátování virtuálních klíčů.

## <a name="syntax"></a>Syntaxe

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Vytvoří `CMFCAcceleratorKey` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CMFCAcceleratorKey::Formát](#format)|Překládá strukturu ACCEL do její vizuální reprezentace.|
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|Nastaví klávesovou `CMFCAcceleratorKey` zkratku pro objekt.|

## <a name="remarks"></a>Poznámky

Klávesy akcelerátoru jsou také známé jako klávesové zkratky. Pokud chcete zobrazit klávesové zkratky, které uživatel zadá, [cmfcacceleratorKeyAssignCtrl třída](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md) mapuje klávesové zkratky, jako je Alt + Shift + S, na vlastní textový formát, například "Alt + Shift + S". Každý `CMFCAcceleratorKey` objekt mapuje jednu klávesovou zkratku na textový formát.

Další informace o použití klávesových zkratek a tabulek akcelerátorů naleznete v [tématu CKeyboardManager Class](../../mfc/reference/ckeyboardmanager-class.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak `CMFCAcceleratorKey` vytvořit objekt a `Format` jak používat jeho metodu.

[!code-cpp[NVC_MFC_RibbonApp#30](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

`CMFCAcceleratorKey`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxacceleratorkey.h

## <a name="cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey

Vytvoří objekt [CMFCAcceleratorKey.](../../mfc/reference/cmfcacceleratorkey-class.md)

```
CMFCAcceleratorKey();
CMFCAcceleratorKey(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parametry

*lpAccel*<br/>
[v] Ukazatel na klávesovou zkratku.

### <a name="remarks"></a>Poznámky

Pokud při vytváření klávesové zkratky `CMFCAccleratorKey`nezadáte , přidružte k `CMFCAcceleratorKey` objektu metodu [CMFCAcceleratorKey::SetAccelerator.](#setaccelerator)

## <a name="cmfcacceleratorkeyformat"></a><a name="format"></a>CMFCAcceleratorKey::Formát

Přeloží strukturu ACCEL na přidruženou hodnotu řetězce.

```cpp
void Format(CString& str) const;
```

### <a name="parameters"></a>Parametry

*Str*<br/>
[out] Odkaz na `CString` objekt, kde metoda zapíše přeloženou klávesovou zkratku.

### <a name="remarks"></a>Poznámky

Tato metoda načte formát řetězce přidružené klávesové zkratky. Můžete nastavit formát řetězce objektu [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) pomocí konstruktoru nebo metody [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator

Nastaví klávesovou zkratku pro objekt [CMFCAcceleratorKey.](../../mfc/reference/cmfcacceleratorkey-class.md)

```cpp
void SetAccelerator(LPACCEL lpAccel);
```

### <a name="parameters"></a>Parametry

*lpAccel*<br/>
[v] Ukazatel na klávesovou zkratku.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete nastavit `CMFCAcceleratorKey` klávesovou zkratku pro a, pokud `CMFCAcceleratorKey`jste při vytváření klávesy nezadali klávesovou zkratku.

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CKeyboardManager – třída](../../mfc/reference/ckeyboardmanager-class.md)
