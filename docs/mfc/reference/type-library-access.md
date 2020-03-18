---
title: Přístup ke knihovně typů
ms.date: 11/04/2016
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
ms.openlocfilehash: 23d4675bd3638d2effd1b967f0729f9e70dac6de
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79420748"
---
# <a name="type-library-access"></a>Přístup ke knihovně typů

Knihovny typů zpřístupňují rozhraní ovládacího prvku OLE jiným aplikacím podporujícím technologii OLE. Pokud je k dispozici jedno nebo více rozhraní, musí mít každý ovládací prvek OLE knihovnu typů.

Následující makra umožňují ovládacímu prvku OLE poskytnout přístup ke své vlastní knihovně typů:

### <a name="type-library-access"></a>Přístup ke knihovně typů

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklaruje členskou funkci `GetTypeLib` ovládacího prvku OLE (musí být použita v deklaraci třídy).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementuje členskou funkci `GetTypeLib` ovládacího prvku OLE (musí být použito v implementaci třídy).|

##  <a name="declare_oletypelib"></a>DECLARE_OLETYPELIB

Deklaruje členskou funkci `GetTypeLib` vaší třídy ovládacího prvku.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku související s knihovnou typů.

### <a name="remarks"></a>Poznámky

Použijte toto makro v souboru hlaviček třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

##  <a name="implement_oletypelib"></a>IMPLEMENT_OLETYPELIB

Implementuje členskou funkci ovládacího prvku `GetTypeLib`.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parametry

*class_name*<br/>
Název třídy ovládacího prvku související s knihovnou typů.

*tlid*<br/>
Číslo ID knihovny typů.

*wVerMajor*<br/>
Číslo hlavní verze knihovny typů

*wVerMinor*<br/>
Číslo dílčí verze knihovny typů

### <a name="remarks"></a>Poznámky

Toto makro se musí nacházet v implementačním souboru pro jakoukoliv třídu ovládacího prvku, která používá makro DECLARE_OLETYPELIB.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
