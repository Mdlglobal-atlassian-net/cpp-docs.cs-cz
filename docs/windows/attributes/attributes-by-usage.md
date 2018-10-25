---
title: Atributy podle použití | Dokumentace Microsoftu
ms.custom: index-page
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI]
ms.assetid: 8be2de10-b1ff-4ca4-a114-75318408593c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7dc5519fbef10ca6c369bcffacacb8351dbc0390
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060426"
---
# <a name="attributes-by-usage"></a>Atributy podle použití

Toto téma obsahuje seznam atributy podle prvky jazyka C++, na které se vztahují.

Pokud atribut předchází element, který není v atributu oboru, je považován za komentář bloku atributu.

|Atribut|Popis|
|---------------|-----------------|
|[Atributy modulu](module-attributes.md)|Platí pro [modulu](module-cpp.md) atribut.|
|[Atributy rozhraní](interface-attributes.md)|Platí pro [__interface](../../cpp/interface.md) – klíčové slovo C++.|
|[Atributy třídy](class-attributes.md)|Platí to – klíčové slovo C++.|
|[Atributy metody](method-attributes.md)|Platí pro metody ve třídě, coclass nebo rozhraní.|
|[Atributy parametru](parameter-attributes.md)|Platí pro parametry metody ve třídě nebo rozhraní.|
|[Atributy datového členu](data-member-attributes.md)|Platí pro datové členy ve třídě, coclass nebo rozhraní.|
|[Atributy klíčových slov typedef, enum, union a struct](typedef-enum-union-and-struct-attributes.md)|Platí pro klíčová slova jazyka C++.|
|[Atributy pole](array-attributes.md)|Platí pro pole nebo `SAFEARRAY`s.|
|[Samostatné atributy](stand-alone-attributes.md)|Informace, jako je například kód funguje, ale nepracuje se klíčové slovo C++. Samostatný atribut příkazy vyžadují středníky na konci řádku.|
|[Vlastní atributy](custom-attributes-cpp.md)|Umožňuje uživateli rozšířit metadat.|

## <a name="module-attributes"></a>Atributy modulu
Tento atribut může být jedině pro [modulu](module-cpp.md) atribut.

|Atribut|Popis|
|---------------|-----------------|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).|

## <a name="interface-attributes"></a>Atributy rozhraní

Následující atributy se vztahují na [rozhraní (nebo __interface)](../../cpp/interface.md) – klíčové slovo C++.

|Atribut|Popis|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Určuje UUID, který nasměruje definovat synchronní a asynchronní verze rozhraní modelu COM kompilátoru MIDL.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atributy.|
|[dispinterface](dispinterface.md)|Umístí rozhraní v souboru IDL jako rozhraní odbavení.|
|[dual](dual.md)|Umístí rozhraní v souboru IDL jako duální rozhraní.|
|[export](export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|
|[helpfile](helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[helpstringcontext](helpstringcontext.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).|
|[hidden](hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[library_block](library-block.md)|Umístí konstrukci uvnitř bloku knihovny souboru IDL.|
|[local](local-cpp.md)|Umožňuje používat v kompilátoru MIDL jako generátor záhlaví při použití v záhlaví rozhraní. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.|
|[nonextensible](nonextensible.md)|Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nejde prodloužit s další členy v době běhu. Tento atribut je platný jenom pro [duální](dual.md) rozhraní.|
|[odl](odl.md)|Označí rozhraní jako objekt popis jazyka (ODL) rozhraní.|
|[object](object-cpp.md)|Určuje vlastní rozhraní.|
|[oleautomation](oleautomation.md)|Označuje, že je kompatibilní s automatizací rozhraní.|
|[pointer_default](pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny odkazy s výjimkou ukazatelů nejvyšší úrovně, které se zobrazí v seznamech parametrů.|
|[ptr](ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[restricted](restricted.md)|Určuje, kteří členové knihovny nejde volat libovolně.|
|[uuid](uuid-cpp-attributes.md)|Poskytuje jedinečné ID pro knihovnu|

Musí dodržovat tato pravidla pro definování rozhraní:

- Je výchozí konvencí volání [__stdcall](../../cpp/stdcall.md).

- Pokud nezadáte jeden identifikátor GUID poskytuje za vás.

- Žádné přetížení metody jsou povoleny.

Pokud nezadáte [uuid](uuid-cpp-attributes.md) atribut a pomocí stejného názvu rozhraní v různých atributů projekty, vygeneruje se stejným GUID.

## <a name="see-also"></a>Viz také

[Atributy C++ pro COM a .NET](cpp-attributes-com-net.md)<br/>
[Atributy podle skupin](attributes-by-group.md)<br/>
[Abecedně řazená referenční dokumentace k atributům](attributes-alphabetical-reference.md)