---
title: Atributy rozhraní (C++ com)
ms.date: 10/02/2018
helpviewer_keywords:
- attributes [C++/CLI], reference topics
- interface attributes
ms.assetid: 27fcdfee-abce-4585-8b53-ee31635356e8
ms.openlocfilehash: 81a88ddfd74f20fa57ef615c988ba9786f41c1ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214822"
---
# <a name="interface-attributes"></a>Atributy rozhraní

Následující atributy se vztahují na klíčové slovo [rozhraní (nebo __interface)](../../cpp/interface.md) C++ .

|Atribut|Popis|
|---------------|-----------------|
|[async_uuid](async-uuid.md)|Určuje identifikátor UUID, který přesměruje kompilátor MIDL tak, aby definoval synchronní i asynchronní verzi rozhraní modelu COM.|
|[custom](custom-cpp.md)|Umožňuje definovat vlastní atributy.|
|[dispinterface](dispinterface.md)|Umístí rozhraní do souboru. idl jako odesílající rozhraní.|
|[dual](dual.md)|Umístí rozhraní do souboru. idl jako duální rozhraní.|
|[export](export.md)|Způsobí, že datová struktura bude umístěna v souboru. idl.|
|[helpcontext](helpcontext.md)|Určuje ID kontextu, které uživateli umožňuje zobrazit informace o tomto prvku v souboru Help.|
|[helpfile](helpfile.md)|Nastaví název souboru s nápovědu pro knihovnu typů.|
|[helpstring](helpstring.md)|Určuje řetězec znaků, který se používá k popisu prvku, na který se vztahuje.|
|[helpstringcontext](helpstringcontext.md)|Určuje ID tématu nápovědy v souboru HLP nebo CHM.|
|[helpstringdll](helpstringdll.md)|Určuje název knihovny DLL, která se má použít k provedení vyhledávání řetězců v dokumentu (lokalizace).|
|[hidden](hidden.md)|Označuje, že položka existuje, ale neměla by se zobrazovat v prohlížeči orientovaném na uživatele.|
|[library_block](library-block.md)|Umístí konstrukci do bloku knihovny souboru. idl.|
|[local](local-cpp.md)|Umožňuje použití kompilátoru MIDL jako generátoru hlaviček při použití v hlavičce rozhraní. Při použití v individuální funkci určí místní proceduru, pro kterou nejsou vygenerována žádná zástupné procedury.|
|[nonextensible](nonextensible.md)|Určuje, že implementace `IDispatch` zahrnuje pouze vlastnosti a metody uvedené v popisu rozhraní a nelze je rozšířit o další členy v době běhu. Tento atribut je platný pouze pro [duální](dual.md) rozhraní.|
|[odl](odl.md)|Identifikuje rozhraní jako rozhraní jazyka Description Language (ODL).|
|[object](object-cpp.md)|Identifikuje vlastní rozhraní.|
|[oleautomation](oleautomation.md)|Označuje, že rozhraní je kompatibilní s automatizací.|
|[pointer_default](pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny ukazatele s výjimkou ukazatelů nejvyšší úrovně, které se zobrazují v seznamech parametrů.|
|[ptr](ptr.md)|Určí ukazatel jako úplný ukazatel.|
|[restricted](restricted.md)|Určuje, kteří členové knihovny nelze volat libovolně.|
|[uuid](uuid-cpp-attributes.md)|Poskytuje jedinečné ID pro knihovnu.|

Musíte dodržovat tato pravidla pro definování rozhraní:

- Výchozí konvence volání je [__stdcall](../../cpp/stdcall.md).

- Identifikátor GUID je zadán za vás, pokud jej nezadáte.

- Nejsou povoleny žádné přetížené metody.

Pokud nezadáte atribut [UUID](uuid-cpp-attributes.md) a použijete stejný název rozhraní v projektech různých atributů, je vygenerován stejný identifikátor GUID.

## <a name="see-also"></a>Viz také

[Atributy podle použití](attributes-by-usage.md)
