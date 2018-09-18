---
title: Řídicí příznaky | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 716e597be5d337d11d58df944bbba468e496f078
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46078059"
---
# <a name="control-flags"></a>Příznaky ovládacích prvků

Ladicí verze knihovny run-time Microsoft C používá následující příznaky do ovládacího prvku přidělení haldy a vytváření sestav procesu. Další informace najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

|Příznak|Popis|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Mapuje na své ekvivalenty ladění verzí funkcí základní haldy|
|[_DEBUG](../c-runtime-library/debug.md)|Umožňuje použití ladění verzí funkcí za běhu|
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Určuje, jak správce hald ladění sleduje přidělení|

Tyto příznaky mohou být definovány pomocí možnosti /D příkazového řádku nebo pomocí `#define` směrnice. Pokud je příznak definován s `#define`, direktiva musí být uvedena před příkaz pro běžné deklarace zahrnout soubor hlaviček.

## <a name="see-also"></a>Viz také

[Globální proměnné a standardní typy](../c-runtime-library/global-variables-and-standard-types.md)