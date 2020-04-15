---
title: Přístup ke knihovně typů
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 1794e16489ab48d919bbd4116588fba4b74b88d9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372876"
---
# <a name="type-library-access"></a>Přístup ke knihovně typů

Knihovny typů zveřejňují rozhraní ovládacího prvku OLE jiným aplikacím podporujícím technologie OLE. Každý ovládací prvek OLE musí mít knihovnu typů, pokud mají být vystaveny jedno nebo více rozhraní.

Následující makra umožňují ovládacímu prvku OLE poskytovat přístup k vlastní knihovně typů:

### <a name="type-library-access"></a>Přístup ke knihovně typů

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklaruje členskou `GetTypeLib` funkci ovládacího prvku OLE (musí být použit v deklaraci třídy).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementuje `GetTypeLib` členskou funkci ovládacího prvku OLE (musí být použitv implementaci třídy).|

## <a name="declare_oletypelib"></a><a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Deklaruje `GetTypeLib` členská funkce třídy ovládacího prvku.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku související s knihovnou typů.

### <a name="remarks"></a>Poznámky

Toto makro použijte v souboru záhlaví třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="implement_oletypelib"></a><a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implementuje členské `GetTypeLib` funkce ovládacího prvku.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku související s knihovnou typů.

*tlid*<br/>
ID číslo knihovny typů.

*wVerMajor*<br/>
Číslo hlavní verze knihovny typů.

*wNeminor*<br/>
Číslo dílčí verze knihovny typů.

### <a name="remarks"></a>Poznámky

Toto makro se musí zobrazit v souboru implementace pro všechny třídy ovládacích prvku, které používají makro DECLARE_OLETYPELIB.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální](../../mfc/reference/mfc-macros-and-globals.md)
