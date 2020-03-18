---
title: DUMPBIN – možnosti
description: Referenční příručka k možnostem příkazového řádku Microsoft DUMPBIN Utility
ms.date: 02/09/2020
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 54f5a22808026f4442f85d5e53a0805702e05868
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440037"
---
# <a name="dumpbin-options"></a>DUMPBIN – možnosti

Možnost se skládá z *specifikátoru možnosti*, který je buď spojovník (`-`), nebo lomítko (`/`) následovaný názvem možnosti. Názvy možností nejde zkracovat. Některé možnosti přijímají argumenty zadané za dvojtečkou (`:`). Ve specifikaci možnosti nejsou povoleny mezery ani tabulátory. Jednotlivé specifikace možností lze na příkazovém řádku oddělit jednou nebo více mezerami či tabulátory. Názvy možností a jejich klíčové slovo nebo argumenty názvu souboru nerozlišují velká a malá písmena. Většina možností se vztahuje na všechny binární soubory, ale v několika případech platí jenom pro určité typy souborů. Ve výchozím nastavení nástroj DUMPBIN odesílá informace do standardního výstupu. K odeslání výstupu do souboru použijte možnost [/out](out-dumpbin.md) .

## <a name="options-list"></a>Seznam možností

Nástroj DUMPBIN obsahuje následující možnosti:

- [/ALL](all.md)

- [/ARCHIVEMEMBERS](archivemembers.md)

- [/CLRHEADER](clrheader.md)

- [/DEPENDENTS](dependents.md)

- [/DIRECTIVES](directives.md)

- [/DISASM\[: počet bajtů\|bajtů}\]](disasm.md)

- [/errorreport: {none | VÝZVA | FRONTA | Odeslat}](errorreport-dumpbin-exe.md) (zastaralé)

- [/EXPORTS](dash-exports.md)

- [/FPO](fpo.md)

- [/HEADERS](headers.md)

- [/IMPORTS\[: filename\]](imports-dumpbin.md)

- [/LINENUMBERS](linenumbers.md)

- [/LINKERMEMBER\[: {1 | 2}\]](linkermember.md)

- [/LOADCONFIG](loadconfig.md)

- [/NOPDB](nopdb.md)

- [/OUT: filename](out-dumpbin.md)

- [/PDATA](pdata.md)

- [/PDBPATH\[: verbose\]](pdbpath.md)

- [/RANGEE: vaMin\[, vaMax\]](range.md)

- [/RAWDATA\[: {NONE\|1\|2\|4\|8}\[, #\]\]](rawdata.md)

- [/RELOCATIONS](relocations.md)

- [/SECTION: název](section-dumpbin.md)

- [/SUMMARY](summary.md)

- [/SYMBOLS](symbols.md)

- [/TLS](tls.md)

Pokud chcete zobrazit seznam možností podporovaných nástrojem DUMPBIN na příkazovém řádku, použijte parametr **/?** . nastavení.

## <a name="see-also"></a>Viz také

[Další nástroje pro sestavení MSVC](c-cpp-build-tools.md)\
\ [příkazového řádku DUMPBIN](dumpbin-command-line.md)
[Odkaz DUMPBIN](dumpbin-reference.md)
