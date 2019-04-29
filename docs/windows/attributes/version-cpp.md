---
title: verze (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.version
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
ms.openlocfilehash: fe1df9e12b9adbf9ce55978fd3479f7e740ddc96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407156"
---
# <a name="version-c"></a>version (C++)

Určuje konkrétní verzi napříč několika verzemi třídu.

## <a name="syntax"></a>Syntaxe

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parametry

*version*<br/>
Číslo verze `coclass`. Pokud není zadán, umístí 1.0 v souboru IDL.

## <a name="remarks"></a>Poznámky

**Verze** C++ atribut má stejné funkce jako [verze](/windows/desktop/Midl/version) atribut MIDL a předána do generovaného souboru.

## <a name="example"></a>Příklad

Najdete v článku [umožňujících vazbu](bindable.md) příklad ukázkový používání **verze**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**Třída**, **– struktura**|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|**coclass**|
|**Neplatné atributy**|Žádné|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Atributy třídy](class-attributes.md)