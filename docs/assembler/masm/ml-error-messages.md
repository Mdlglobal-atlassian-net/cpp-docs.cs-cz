---
title: Chybové zprávy nástroje ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
ms.openlocfilehash: aa0440afae980e218c32ab3296bd7c6fb2b444d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677796"
---
# <a name="ml-error-messages"></a>Chybové zprávy nástroje ML

Chybové zprávy generované komponentami MASM spadají do tří kategorií:

- **Závažné chyby.** Tyto zprávy značí závažný problém, který zabrání dokončení jeho normální proces nástroj.

- **Méně závažné chyby.** Nástroj může dokončit jeho proces. Pokud ano, není výsledek bude ten, který chcete.

- **Upozornění.** Tyto zprávy určují podmínky, které můžou bránit získání požadovaných výsledků.

Všechny chybové zprávy následující podobu:

> *Nástroj*: *Filename* (*řádku*): {*error_type –*} (*kód*): *Message_text*

kde:

*Nástroj*<br/>
Program, který odeslal zprávu chyby.

*Název souboru*<br/>
Soubor, který obsahuje podmínku chyby generování.

*Řádek*<br/>
Přibližná řádku, kde existenci chybového stavu.

*Error_type –*<br/>
Závažná chyba, chyba nebo upozornění.

*Kód*<br/>
Kód chyby jedinečný 5 nebo 6číslice.

*Message_text*<br/>
Popis krátký a obecné chybového stavu.

## <a name="see-also"></a>Viz také:

[Microsoft Macro Assembler – referenční dokumentace](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>