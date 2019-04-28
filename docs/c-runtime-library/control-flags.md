---
title: Příznaky ovládacích prvků
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- flags, control
- heap allocation, control flags
- debug heap, control flags
ms.assetid: 8dbd24a5-0633-42d1-9771-776db338465f
ms.openlocfilehash: 7ac5f239ea4d242618fb23ba617a3a6539492053
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62344756"
---
# <a name="control-flags"></a>Příznaky ovládacích prvků

Ladicí verze knihovny run-time Microsoft C používá následující příznaky do ovládacího prvku přidělení haldy a vytváření sestav procesu. Další informace najdete v tématu [techniky ladění CRT](/visualstudio/debugger/crt-debugging-techniques).

|Příznak|Popis|
|----------|-----------------|
|[_CRTDBG_MAP_ALLOC](../c-runtime-library/crtdbg-map-alloc.md)|Mapuje na své ekvivalenty ladění verzí funkcí základní haldy|
|[_DEBUG](../c-runtime-library/debug.md)|Umožňuje použití ladění verzí funkcí za běhu|
|[_crtDbgFlag](../c-runtime-library/crtdbgflag.md)|Určuje, jak správce hald ladění sleduje přidělení|

Tyto příznaky mohou být definovány pomocí možnosti /D příkazového řádku nebo pomocí `#define` směrnice. Pokud je příznak definován s `#define`, direktiva musí být uvedena před příkaz pro běžné deklarace zahrnout soubor hlaviček.

## <a name="see-also"></a>Viz také:

[Globální proměnné a standardní typy](../c-runtime-library/global-variables-and-standard-types.md)
