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
ms.openlocfilehash: ee79fca8784ade6509cfc5854eaaa165b68edee0
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789531"
---
# <a name="version-c"></a>version (C++)

Určuje konkrétní verzi napříč několika verzemi třídu.

## <a name="syntax"></a>Syntaxe

```cpp
[ version("version") ]
```

### <a name="parameters"></a>Parametry

*Verze*<br/>
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