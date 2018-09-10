---
title: Atributy rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 850646e2dda1f226eff7c921dd3fe9f85595ca69
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44317651"
---
# <a name="interface-attributes"></a>Atributy rozhraní

Následující atributy se vztahují na [rozhraní (nebo __interface)](../cpp/interface.md) – klíčové slovo C++.

|Atribut|Popis|
|---------------|-----------------|
|[async_uuid](../windows/async-uuid.md)|Určuje UUID, který nasměruje definovat synchronní a asynchronní verze rozhraní modelu COM kompilátoru MIDL.|
|[Vlastní](../windows/custom-cpp.md)|Umožňuje definovat vlastní atributy.|
|[dispinterface](../windows/dispinterface.md)|Umístí rozhraní v souboru IDL jako rozhraní odbavení.|
|[dual](../windows/dual.md)|Umístí rozhraní v souboru IDL jako duální rozhraní.|
|[export](../windows/export.md)|Způsobí, že datová struktura budou umístěny v souboru IDL.|
|[helpcontext](../windows/helpcontext.md)|Určuje ID kontextu, který umožňuje uživateli zobrazit informace o tomto prvku v souboru nápovědy.|
|[helpfile](../windows/helpfile.md)|Nastaví název souboru nápovědy pro knihovnu typů.|
|[helpstring](../windows/helpstring.md)|Určuje řetězec znaků, který se používá k popisu elementu, ke kterému se vztahuje.|
|[helpstringcontext](../windows/helpstringcontext.md)|Určuje ID tématu nápovědy HLP nebo CHM souboru.|
|[helpstringdll](../windows/helpstringdll.md)|Určuje název knihovny DLL použít k provádění vyhledání řetězce dokumentu (lokalizace).|
|[hidden](../windows/hidden.md)|Označuje, že položka existuje, ale nebude se zobrazovat v prohlížeči uživatele.|
|[library_block](../windows/library-block.md)|Umístí konstrukci uvnitř bloku knihovny souboru IDL.|
|[místní](../windows/local-cpp.md)|Umožňuje používat v kompilátoru MIDL jako generátor záhlaví při použití v záhlaví rozhraní. Při použití jednotlivých funkcí, určuje místní postupu, pro které jsou generovány žádné zástupné procedury.|
|[nonextensible](../windows/nonextensible.md)|Určuje, že `IDispatch` implementace obsahuje pouze vlastnosti a metody uvedené v popisu rozhraní a nejde prodloužit s další členy v době běhu. Tento atribut je platný jenom pro [duální](../windows/dual.md) rozhraní.|
|[odl](../windows/odl.md)|Označí rozhraní jako objekt popis jazyka (ODL) rozhraní.|
|[object](../windows/object-cpp.md)|Určuje vlastní rozhraní.|
|[oleautomation](../windows/oleautomation.md)|Označuje, že je kompatibilní s automatizací rozhraní.|
|[pointer_default](../windows/pointer-default.md)|Určuje výchozí atribut ukazatele pro všechny odkazy s výjimkou ukazatelů nejvyšší úrovně, které se zobrazí v seznamech parametrů.|
|[ptr](../windows/ptr.md)|Ukazatel se označí jako úplné ukazatel.|
|[restricted](../windows/restricted.md)|Určuje, kteří členové knihovny nejde volat libovolně.|
|[uuid](../windows/uuid-cpp-attributes.md)|Poskytuje jedinečné ID pro knihovnu|

Musí dodržovat tato pravidla pro definování rozhraní:

- Je výchozí konvencí volání [__stdcall](../cpp/stdcall.md).

- Pokud nezadáte jeden identifikátor GUID poskytuje za vás.

- Žádné přetížení metody jsou povoleny.

Pokud nezadáte [uuid](../windows/uuid-cpp-attributes.md) atribut a pomocí stejného názvu rozhraní v různých atributů projekty, vygeneruje se stejným GUID.

## <a name="see-also"></a>Viz také

[Atributy podle použití](../windows/attributes-by-usage.md)