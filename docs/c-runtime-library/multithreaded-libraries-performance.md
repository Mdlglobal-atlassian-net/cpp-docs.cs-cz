---
title: Výkon vícevláknových knihoven | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- threading [C++], performance
- libraries, multithreaded
- performance, multithreading
- multithreaded libraries
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f66aebc7b6d77e3697fabf783332a83bdd6f3fb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052100"
---
# <a name="multithreaded-libraries-performance"></a>Výkon vícevláknových knihoven

S jedním vláknem CRT již není k dispozici. Toto téma popisuje, jak získat maximální výkon z vícevláknových knihoven.

## <a name="maximizing-performance"></a>Dosažení maximálního výkonu

Výkon vícevláknových knihoven byla vylepšena a je blízko výkonu knihovny odstranili nyní s jedním vláknem. Pro tyto situace, kdy je nutná, dokonce i vyšší výkon existují několik nových funkcí.

- Uzamčení nezávislé stream umožňuje uzamknout datového proudu a pak použijte [_nolock – funkce](../c-runtime-library/nolock-functions.md) , který přímo přístup k datovému proudu. To umožňuje zámku informací o využití a zdvihnut mimo kritické smyčky.

- Národní prostředí jednotlivých vláken snižuje náklady na přístup národní prostředí pro scénáře s více vlákny (viz [_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)).

- Funkce závislé na národním prostředí (s názvy končící na _l) přijímají národní prostředí jako parametr, odebrání značné náklady (například [printf _printf_l –, wprintf _wprintf_l –](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)).

- Optimalizace pro běžné neurčují snížit náklady na krátké mnoho operací.

- Definování [_CRT_DISABLE_PERFCRIT_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) vynutí všechny vstupně-výstupních operací předpokládají vstupně-výstupních operací modelu s jedním vláknem a používání formulářů _nolock – funkce. To umožňuje vysoce I O založené na/jednovláknový aplikacím dosahovat vyšších výkonů.

- Vystavení popisovač haldy CRT umožňuje povolit Windows s nízkou fragmentací haldy (LFH) pro haldu CRT, což může výrazně zvýšit výkon vysoce přizpůsobený scénáře.

## <a name="see-also"></a>Viz také

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)