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
ms.openlocfilehash: 7d66e7043325bbbd324f3ac443368787a653ebe1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369927"
---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey – třída

Pomocná třída, která implementuje mapování a formátování virtuálních klíčů.

## <a name="syntax"></a>Syntaxe

```
class CMFCAcceleratorKey : public CObject
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|Vytvoří `CMFCAcceleratorKey` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
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

```
void Format(CString& str) const;
```

### <a name="parameters"></a>Parametry

*Str*<br/>
[out] Odkaz na `CString` objekt, kde metoda zapíše přeloženou klávesovou zkratku.

### <a name="remarks"></a>Poznámky

Tato metoda načte formát řetězce přidružené klávesové zkratky. Můžete nastavit formát řetězce objektu [CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md) pomocí konstruktoru nebo metody [CMFCAcceleratorKey::SetAccelerator](#setaccelerator).

## <a name="cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator

Nastaví klávesovou zkratku pro objekt [CMFCAcceleratorKey.](../../mfc/reference/cmfcacceleratorkey-class.md)

```
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
