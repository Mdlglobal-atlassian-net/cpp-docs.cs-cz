---
title: /ERRORREPORT (editbin.exe)
description: Referenční informace pro možnost příkazového řádku Microsoft nástroje EDITBIN Utility
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT_editbin
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 4456a49cc53b21bd24c616852159ca299181071b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439897"
---
# <a name="errorreport-editbinexe"></a>/ERRORREPORT (editbin.exe)

> [!NOTE]
> Možnost/ERRORREPORT je zastaralá. Od Windows Vista se hlášení chyb řídí nastavením [zasílání zpráv o chybách systému Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Syntaxe

> **/Errorreport** \[ **NONE** \| **prompt** \| **Queue** \| **Send** ]

## <a name="remarks"></a>Poznámky

Argumenty **/errorreport** jsou přepsané nastavením služby zasílání zpráv o chybách systému Windows. NÁSTROJE EDITBIN automaticky odesílá zprávy o interních chybách společnosti Microsoft, pokud je služba Reporting povolena Zasílání zpráv o chybách systému Windows. Pokud je zakázána Zasílání zpráv o chybách systému Windows, není odeslána žádná sestava.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](editbin-options.md)
