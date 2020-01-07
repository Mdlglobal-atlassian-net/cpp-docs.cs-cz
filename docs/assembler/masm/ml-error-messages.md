---
title: Chybové zprávy nástroje ML
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: 1b065433a1a6baf9bf2631aeb2f53421f8efb83b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312622"
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

[Microsoft Macro Assembler – referenční dokumentace](microsoft-macro-assembler-reference.md)
