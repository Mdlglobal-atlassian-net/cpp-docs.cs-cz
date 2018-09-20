---
title: Obecné jazykové změny (C + +/ CLI) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9b48ebdf0bf25399b08f8a1cb1240a857cfad352
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418453"
---
# <a name="general-language-changes-ccli"></a>Obecné jazykové změny (C++/CLI)

Počet funkcí jazyka CLR změněn ze spravovaného rozšíření jazyka C++ pro Visual C++.

Změny popisované v této části jsou řazení směsicí jazyka. Zahrnuje změnu ve zpracování řetězcové literály, změny v řešení přetížení mezi třemi tečkami a `Param` změna z atributu `typeof` k `typeid`, změny se vyvolat seznamy inicializátorů konstruktorů a zavedení nový zápis přetypování u `safe_cast`.

[Řetězcový literál](../dotnet/string-literal.md)<br/>
Tento článek popisuje, jak došlo ke změně zpracování řetězcové literály.

[Pole parametrů a tři tečky](../dotnet/param-array-and-ellipsis.md)<br/>
Popisuje, jak `ParamArray` je nyní přednost nad třemi tečkami (`...`) pro vyřešení funkce volání s proměnlivým počtem argumentů.

[typeof přechází na T::typeid](../dotnet/typeof-goes-to-t-typeid.md)<br/>
Popisuje, jak `typeof` byl nahrazen operátor `typeid`.

[Seznamy inicializátorů](../dotnet/initializer-lists.md)<br/>
Tento článek popisuje změny v pořadí volání seznamy inicializátorů.

[Zápis přetypování a úvod do operace safe_cast<>](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)<br/>
Tento článek popisuje změny na zápis přetypování a zejména po zavedení služby `safe_cast`.

## <a name="see-also"></a>Viz také

[Základy migrace v jazyce C++/CLI](../dotnet/cpp-cli-migration-primer.md)