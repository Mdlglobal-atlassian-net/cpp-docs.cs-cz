---
title: Chybové zprávy nástroje ML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- vc.errors.ml
dev_langs:
- C++
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), ML error messages
ms.assetid: e7e164b3-6d65-4b5b-8925-bfbebc043523
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 836daf438fa5a7f4c797b5b15ffab89720a7af98
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43675962"
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