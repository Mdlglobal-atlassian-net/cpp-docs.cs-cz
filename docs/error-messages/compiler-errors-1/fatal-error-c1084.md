---
title: Závažná chyba C1084
ms.date: 11/04/2016
f1_keywords:
- C1084
helpviewer_keywords:
- C1084
ms.assetid: b2f273ef-3a14-4d5f-8ce0-7a11a0388fe6
ms.openlocfilehash: b0c8e6a8f8321dccdfd7cee128a4cf06cebda991
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501131"
---
# <a name="fatal-error-c1084"></a>Závažná chyba C1084

Nedá se přečíst soubor typ_souboru: File: Message.

Tato chyba je obvykle výsledkem neúspěšného volání rozhraní API interního systému provedeného kompilátorem. Zpráva zobrazená v případě výskytu této chyby je často generována buď [_wcserror_s](../../c-runtime-library/reference/strerror-s-strerror-s-wcserror-s-wcserror-s.md) nebo [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage).

Následující kroky vám pomůžou vyřešit C1084:

- Zajistěte, aby zadaný soubor existoval.

- Zajistěte, aby byla pro přístup k zadanému souboru nastavena příslušná oprávnění.

- Zajistěte, aby syntaxe příkazového řádku odpovídala pravidlům popsaným v části [syntaxe příkazového řádku kompilátoru](../../build/reference/compiler-command-line-syntax.md).

- Zajistěte, aby byly správně nastaveny proměnné prostředí **TMP** a **TEMP** , a také příslušná oprávnění, aby bylo možné získat přístup k adresářům, na které tyto proměnné prostředí odkazují. Také zajistěte, aby jednotky, na které odkazují proměnné prostředí **TMP** a **TEMP** , obsahovaly dostatečné množství volného místa.

- Pokud se v této zprávě zobrazí zpráva "špatné číslo souboru", zadaný soubor mohl být při kompilování na pozadí uzavřený v popředí.

Po provedení výše uvedených diagnostických nástrojů proveďte čisté sestavení.