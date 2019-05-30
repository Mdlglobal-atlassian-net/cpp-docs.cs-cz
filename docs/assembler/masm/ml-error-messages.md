---
title: Chybové zprávy nástroje ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: adf2c509c3d8d9110ddb757f809a4bca9199df7a
ms.sourcegitcommit: af580f3a11b19d22288424eac7ceae1bc24ab312
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66355327"
---
# <a name="ml-error-messages"></a>Chybové zprávy nástroje ML

Chybové zprávy generované komponentami MASM spadají do tří kategorií:

- **Závažné chyby.** Tyto zprávy značí závažný problém, který zabrání dokončení jeho normální proces nástroj.

- **Méně závažné chyby.** Nástroj může dokončit jeho proces. Pokud ano, není výsledek bude ten, který chcete.

- **Upozornění.** Tyto zprávy určují podmínky, které můžou bránit získání požadovaných výsledků.

Všechny chybové zprávy následující podobu:

> *Nástroj*: *Filename* (*Line*) : {*Error_type*} (*Code*): *Message_text*

kde:

*Nástroj*<br/>
Program, který odeslal zprávu chyby.

*Název souboru*<br/>
Soubor, který obsahuje podmínku chyby generování.

*Řádek*<br/>
Přibližná řádku, kde existenci chybového stavu.

*Error_type*<br/>
Závažná chyba, chyba nebo upozornění.

*Kód*<br/>
Kód chyby jedinečný 5 nebo 6číslice.

*Message_text*<br/>
Popis krátký a obecné chybového stavu.

## <a name="see-also"></a>Viz také:

[Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)
