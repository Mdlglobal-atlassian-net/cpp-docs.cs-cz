---
title: /ERRORREPORT (dumpbin.exe)
description: Referenční informace pro možnost příkazového řádku Microsoft DUMPBIN Utility/ERRORREPORT
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT_dumpbin
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: f701c2e28dcf82194589877709bf6959de4bcbfc
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439930"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT (dumpbin.exe)

> [!NOTE]
> Možnost/ERRORREPORT je zastaralá. Od Windows Vista se hlášení chyb řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Syntaxe

> **/Errorreport**\[**NONE** \| **prompt** \| **Queue** \| **Send** ]

## <a name="remarks"></a>Poznámky

Argumenty **/errorreport** jsou přepsané nastavením služby zasílání zpráv o chybách systému Windows. Služba DUMPBIN automaticky odesílá zprávy o interních chybách společnosti Microsoft, pokud je služba Reporting povolena Zasílání zpráv o chybách systému Windows. Pokud je zakázána Zasílání zpráv o chybách systému Windows, není odeslána žádná sestava.

## <a name="see-also"></a>Viz také

[DUMPBIN – možnosti](dumpbin-options.md)
