---
title: usesgetlasterror – (atribut C++ COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.usesgetlasterror
helpviewer_keywords:
- usesgetlasterror attribute
ms.assetid: d149e33d-35a7-46cb-9137-ae6883d86122
ms.openlocfilehash: 9f050bbf69edf1ab8327a283299cb5e687ce5380
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59032203"
---
# <a name="usesgetlasterror"></a>usesgetlasterror

Říká volajícímu, že pokud dojde k chybě při volání této funkce, potom volající provést zavoláním `GetLastError` načíst kód chyby.

## <a name="syntax"></a>Syntaxe

```cpp
[usesgetlasterror]
```

## <a name="remarks"></a>Poznámky

**Usesgetlasterror –** C++ atribut má stejné funkce jako [usesgetlasterror –](/windows/desktop/Midl/usesgetlasterror) atribut MIDL.

## <a name="example"></a>Příklad

Zobrazit [možnost idl_module](idl-module.md) příklad ukázku toho, jak používat **usesgetlasterror –**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Atribut kontextu

|||
|-|-|
|**Platí pro**|**modul** atribut|
|**Opakovatelné**|Ne|
|**Vyžadované atributy**|Žádné|
|**Neplatné atributy**|Žádný|

Další informace o kontexty atributů najdete v tématu [kontexty atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)