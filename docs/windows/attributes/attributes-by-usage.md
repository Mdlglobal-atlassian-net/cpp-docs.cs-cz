---
title: Atributy podle použití
ms.custom: index-page
ms.date: 10/02/2018
ms.topic: conceptual
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
ms.openlocfilehash: dcbed019f8cd08ddbf4ab6b4756a59f7fcbabc4b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81361339"
---
# <a name="attributes-by-usage"></a>Atributy podle použití

Toto téma uvádí atributy podle prvků jazyka C++, na které se vztahují.

Pokud atribut předchází prvek, který není v oboru atributu, blok atributu je považován za komentář.

|Atribut|Popis|
|---------------|-----------------|
|[Atributy modulu](module-attributes.md)|Platí pro atribut [modulu.](module-cpp.md)|
|[Atributy rozhraní](interface-attributes.md)|Platí pro [klíčové](../../cpp/interface.md) slovo __interface C++.|
|[Atributy třídy](class-attributes.md)|Platí pro klíčové slovo C++.|
|[Atributy metody](method-attributes.md)|Platí pro metody ve třídě, coclass nebo rozhraní.|
|[Atributy parametrů](parameter-attributes.md)|Platí pro parametry metody ve třídě nebo rozhraní.|
|[Atributy datového členu](data-member-attributes.md)|Platí pro datové členy ve třídě, coclass nebo rozhraní.|
|[Atributy Typedef, Enum, Union a Struct](typedef-enum-union-and-struct-attributes.md)|Platí pro klíčová slova jazyka C++.|
|[Atributy pole](array-attributes.md)|Platí pro pole `SAFEARRAY`nebo s.|
|[Samostatné atributy](stand-alone-attributes.md)|Funguje spíše jako řádek kódu, ale nepracuje s klíčovým slovem Jazyka C++. Samostatné příkazy atributů vyžadují středník na konci řádku.|
|[Vlastní atributy](custom-attributes-cpp.md)|Umožňuje uživateli rozšířit metadata.|

## <a name="module-attributes"></a>Atributy modulu

Následující atribut lze použít pouze pro atribut [modulu.](module-cpp.md)

|Atribut|Popis|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL, která má být používána k provedení vyhledávání řetězce dokumentu (lokalizace).|

## <a name="interface-attributes"></a>Atributy rozhraní

Následující atributy platí pro klíčové slovo [rozhraní (nebo __interface)](../../cpp/interface.md) C++.

|Atribut|Popis|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Určuje uuid, který nasměruje kompilátor MIDL k definování synchronních i asynchronních verzí rozhraní COM.|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atributy.|
|[dispinterface](dispinterface.md)|Umístí rozhraní do souboru .idl jako odeslání rozhraní.|
|[dual](dual.md)|Umístí rozhraní do souboru .idl jako duální rozhraní.|
|[Vývozní](export.md)|Způsobí, že do souboru IDL bude umístěna datová struktura.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, které umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|
|[helpfile](helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje.|
|[helpstringcontext](helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL, která má být používána k provedení vyhledávání řetězce dokumentu (lokalizace).|
|[Skryté](hidden.md)|Označuje, že položka existuje, ale neměla by být zobrazena v prohlížeči orientovaném na uživatele.|
|[library_block](library-block.md)|Umístí konstrukci do bloku knihovny souboru .idl.|
|[Místní](local-cpp.md)|Umožňuje použít kompilátor MIDL jako generátor záhlaví při použití v hlavičce rozhraní. Při použití v jednotlivé funkce, označuje místní postup, pro které jsou generovány žádné zástupné procedury.|
|[nonextensible](nonextensible.md)|Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze je rozšířit o další členy za běhu. Tento atribut je platný pouze na [duální](dual.md) rozhraní.|
|[odl](odl.md)|Identifikuje rozhraní jako rozhraní jazyka POPISU objektu (ODL).|
|[Objekt](object-cpp.md)|Identifikuje vlastní rozhraní.|
|[oleautomation](oleautomation.md)|Označuje, že rozhraní je kompatibilní s automatizací.|
|[pointer_default](pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny ukazatele kromě ukazatelů nejvyšší úrovně, které se zobrazují v seznamech parametrů.|
|[Ptr](ptr.md)|Označuje ukazatel jako úplný ukazatel.|
|[restricted](restricted.md)|Určuje, které členy knihovny nelze volat libovolně.|
|[Uuid](uuid-cpp-attributes.md)|Poskytuje jedinečné ID pro knihovnu.|

Je nutné dodržovat tato pravidla pro definování rozhraní:

- Výchozí konvence volání je [__stdcall](../../cpp/stdcall.md).

- Identifikátor GUID je dodáván za vás, pokud ji nedodáváte.

- Nejsou povoleny žádné přetížené metody.

Pokud není zadán [uuid](uuid-cpp-attributes.md) atribut a pomocí stejného názvu rozhraní v různých projektech atributů, je generován stejný identifikátor GUID.

## <a name="see-also"></a>Viz také

[Atributy C++ pro COM a .NET](cpp-attributes-com-net.md)<br/>
[Atributy podle skupin](attributes-by-group.md)<br/>
[Atributy abecední odkaz](attributes-alphabetical-reference.md)
