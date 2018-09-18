---
title: Bajtové a široké proudy | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- Byte and Wide Streams
dev_langs:
- C++
helpviewer_keywords:
- byte streams
- wide streams
ms.assetid: 61ef0587-4cbc-4eb8-aae5-4c298dbbc6f9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e031aa0ebbad279c630f2687457af11dc478b72d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46095830"
---
# <a name="byte-and-wide-streams"></a>Bajtové a široké proudy

Datový proud bajtů zpracovává soubor jako sekvence bajtů. V rámci programu je datový proud stejné pořadí bajtů.

Naopak široké stream považuje za soubor posloupnost zobecněný vícebajtových znaků, což může mít celou řadu kódování pravidla. (Textové a binární soubory jsou nadále číst a zapisovat jak bylo popsáno dříve.) V rámci programu datového proudu vypadá jako odpovídající pořadí širokých znaků. Převody mezi dvěma reprezentace dojít v rámci standardní knihovny jazyka C. Pravidla převodu lze v zásadě, změnit voláním [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) , který mění kategorii `LC_CTYPE`. Každý datový proud široké určuje jeho pravidla převodu v době, bude celý orientované a uchovává tyto pravidla i v případě kategorii `LC_CTYPE` následně změní.

Umístění v rámci široké datového proudu utrpí stejná omezení jako text steams. Kromě toho Indikátor pozice v souboru může mít také řešit závislá na stavu kódování. Obvykle obsahuje oba posun v bajtech v rámci datový proud a objekt typu `mbstate_t`. Proto pouze spolehlivý způsob, jak získat pozice souboru v rámci široké datového proudu je voláním [fgetpos](../c-runtime-library/reference/fgetpos.md), a pouze spolehlivý způsob, jak obnovit pozici získat tímto způsobem je voláním [fsetpos](../c-runtime-library/reference/fsetpos.md).

## <a name="see-also"></a>Viz také

[Soubory a proudy](../c-runtime-library/files-and-streams.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)