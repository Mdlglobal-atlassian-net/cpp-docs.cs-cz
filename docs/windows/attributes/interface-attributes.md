---
title: Atributy (C++ COM) rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/02/2018
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cd12db4235d22245c3f31ce7dfe3fd2470133dfd
ms.sourcegitcommit: 955ef0f9d966e7c9c65e040f1e28fa83abe102a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48789355"
---
# <a name="interface-attributes"></a>Atributy rozhraní

Následující atributy se vztahují na [rozhraní (nebo __interface)](../../cpp/interface.md) – klíčové slovo C++.

|Atribut|Popis|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Určuje UUID, který nasměruje definovat synchronní a asynchronní verze rozhraní modelu COM kompilátoru MIDL.|
|[Vlastní](custom-cpp.md)|Umožňuje definovat vlastní atributy.|
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
|[místní](local-cpp.md)|Umožňuje používat v kompilátoru MIDL jako generátor záhlaví při použití v záhlaví rozhraní. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.|
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

[Atributy podle použití](attributes-by-usage.md)