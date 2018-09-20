---
title: Zadejte přístup ke knihovně | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.macros
dev_langs:
- C++
helpviewer_keywords:
- type libraries [MFC], accessing
ms.assetid: a03fa7f0-86c2-4119-bf81-202916fb74b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1a361c1e50945b19562082424c178a21191bd0b9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46404734"
---
# <a name="type-library-access"></a>Přístup ke knihovně typů

Knihovny typů zveřejňují rozhraní ovládacího prvku OLE do jiných aplikací pracujících s OLE. Pokud jedno nebo více rozhraní se zpřístupní, musí mít každý ovládací prvek OLE knihovnu typů.

Následující makra povolit ovládacího prvku OLE a zajistit tak přístup do své vlastní knihovny typů:

### <a name="type-library-access"></a>Přístup ke knihovně typů

|||
|-|-|
|[DECLARE_OLETYPELIB](#declare_oletypelib)|Deklaruje `GetTypeLib` členské funkce ovládacího prvku OLE (musí se použít v deklaraci třídy).|
|[IMPLEMENT_OLETYPELIB](#implement_oletypelib)|Implementuje `GetTypeLib` členské funkce ovládacího prvku OLE (musí být použitý v implementaci třídy).|

##  <a name="declare_oletypelib"></a>  DECLARE_OLETYPELIB

Deklaruje `GetTypeLib` členské funkce třídy ovládacího prvku.

```
DECLARE_OLETYPELIB(class_name)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku související do knihovny typů.

### <a name="remarks"></a>Poznámky

Použijte toto makro v souboru hlaviček třídy ovládacího prvku.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

##  <a name="implement_oletypelib"></a>  IMPLEMENT_OLETYPELIB

Implementuje ovládací prvek `GetTypeLib` členskou funkci.

```
IMPLEMENT_OLETYPELIB(class_name, tlid, wVerMajor,  wVerMinor)
```

### <a name="parameters"></a>Parametry

*$class_name*<br/>
Název třídy ovládacího prvku související do knihovny typů.

*tlid*<br/>
Číslo ID knihovny typů.

*wvermajor –*<br/>
Číslo hlavní verze knihovny typů.

*wverminor –*<br/>
Číslo podverze knihovny typů.

### <a name="remarks"></a>Poznámky

Toto makro musí být uvedena v souboru implementace pro ovládací prvek třídy, které používá DECLARE_OLETYPELIB – makro.

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxdisp.h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md)
