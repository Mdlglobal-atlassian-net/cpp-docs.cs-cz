---
title: DUMPBIN – možnosti
ms.date: 10/24/2019
f1_keywords:
- dumpbin
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 81c66f1971294531a2904a0b681819476bcc1eb2
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144554"
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

- [/ERRORREPORT: {NONE | VÝZVA | FRONTA | POSÍLAJÍ](errorreport-dumpbin-exe.md)

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

## <a name="see-also"></a>Viz také:

[Další nástroje pro sestavení MSVC](c-cpp-build-tools.md)\
\ [příkazového řádku DUMPBIN](dumpbin-command-line.md)
[Odkaz DUMPBIN](dumpbin-reference.md)
