---
title: ProgID (C++ atribut com)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.progid
helpviewer_keywords:
- progid attribute
ms.assetid: afcf559c-e432-481f-aa9a-bd3bb72c02a8
ms.openlocfilehash: d529d7362dc62207cfd72576159f560a3e04c221
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514245"
---
# <a name="progid"></a>progid

Určuje identifikátor ProgID pro objekt modelu COM.

## <a name="syntax"></a>Syntaxe

```cpp
[ progid(name) ];
```

### <a name="parameters"></a>Parametry

*name*<br/>
Identifikátor ProgID představující objekt

Identifikátory ProgID prezentují uživatelsky čitelné verze identifikátoru třídy (CLSID) používané k identifikaci objektů COM/ActiveX.

## <a name="remarks"></a>Poznámky

Atribut **ProgID** C++ umožňuje zadat identifikátor ProgID pro objekt modelu COM. Identifikátor ProgID má formu *název1. název2. Version*. Pokud nezadáte *verzi* pro identifikátor ProgID, je výchozí verze 1. Pokud nezadáte *název1. název2*, výchozí název je *ClassName. ClassName*. Pokud neurčíte **ProgID** a zadáte `vi_progid`, bude získána hodnota *název1. název2* z `vi_progid` a připojená verze (další sekvenční číslo).

Pokud blok atributu, který používá **ProgID** , nepoužívá také **identifikátor UUID**, kompilátor zkontroluje registr a zjistí, zda **identifikátor UUID** pro zadaný **identifikátor ProgID**existuje. Pokud není zadán parametr **ProgID** , verze (a název třídy coclass, při vytváření třídy coclass) budou použity k vygenerování **identifikátoru ProgID**.

**identifikátor ProgID** implikuje `coclass` atribut, to znamená, že pokud zadáte **ProgID**, je totéž jako zadání `coclass` atributů a atributy **ProgID** .

Atribut **ProgID** způsobí, že se třída automaticky zaregistruje pod zadaným názvem. Ve vygenerovaném souboru. idl se nezobrazí hodnota **ProgID** .

Při použití tohoto atributu v projektu, který používá ATL, se chování atributu změní. Kromě výše uvedeného chování jsou informace zadané pomocí tohoto atributu použity ve `GetProgID` funkci, vloženy `coclass` atributem. Další informace naleznete v tématu atribut [Coclass](coclass.md) .

## <a name="example"></a>Příklad

Viz příklad pro [třídu coclass](coclass.md) pro ukázkové použití **ProgID**.

## <a name="requirements"></a>Požadavky

### <a name="attribute-context"></a>Kontext atributu

|||
|-|-|
|**Platí pro**|**Třída**, **Struktura**|
|**REPEATABLE**|Ne|
|**Požadované atributy**|Žádné|
|**Neplatné atributy**|Žádné|

Další informace o kontextech atributů naleznete v tématu kontexty [atributů](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Viz také:

[IDL – atributy](idl-attributes.md)<br/>
[Atributy třídy](class-attributes.md)<br/>
[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)<br/>
[Klíč ProgID](/windows/win32/com/-progid--key)
