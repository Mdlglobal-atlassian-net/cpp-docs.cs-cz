---
title: Chybové zprávy nástroje ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: b9238591ae025c4af258d8b5feda6e05c8bd291b
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397180"
---
# <a name="ml-error-messages"></a>Chybové zprávy nástroje ML

Chybové zprávy generované součástmi MASM spadají do tří kategorií:

- **Závažné chyby.** Tyto označují vážný problém, který brání nástroji v dokončení normálního procesu.

- **Méně závažné chyby** Nástroj může dokončit svůj proces. Pokud k tomu dojde, jeho výsledek nebude pravděpodobně ten, který chcete.

- **Varování.** Tyto zprávy označují podmínky, které vám můžou zabránit v získání výsledků, které chcete.

Všechny chybové zprávy mají následující formát:

> *Nástroj*: *filename* (*line*): {*Error_type*} (*kód*): *Message_text*

kde:

\ *nástrojů*
Program, který odeslal chybovou zprávu.

*Název souboru*\
Soubor, který obsahuje podmínku generování chyb.

\ *řádku*
Přibližná čára, kde chybový stav existuje.

*Error_type*\
Závažná chyba, chyba nebo upozornění.

\ *kódu*
Jedinečný kód chyby 5 nebo 6 číslic.

*Message_text*\
Krátký a obecný popis chybové podmínky.

## <a name="see-also"></a>Viz také:

[Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)
