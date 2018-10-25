---
title: verze (atribut C++ COM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- vc-attr.version
dev_langs:
- C++
helpviewer_keywords:
- version attribute
- version information, version attribute
ms.assetid: db6ce5d8-82c2-4329-b1a8-8ca2f67342cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95b30d65fe67f2647cb8ca50619f3ab13f167053
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50058996"
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

## <a name="see-also"></a>Viz také

[Atributy kompilátoru](compiler-attributes.md)<br/>
[Atributy třídy](class-attributes.md)