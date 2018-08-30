---
title: Chyba sestavení projektu PRJ0002 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0002
dev_langs:
- C++
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc0e48130c17e04c2671395161452c9e66000047
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195712"
---
# <a name="project-build-error-prj0002"></a>Chyba sestavení projektu PRJ0002

> Chyba výsledek vrácený z "*příkazového řádku*".

V příkazu *příkazového řádku*, který byl vytvořen ze vstupu uživatele v **stránky vlastností** zobrazí se v dialogovém okně vrátil kód chyby, ale žádné informace o **výstup** okna .

Řešení této chyby závisí na který nástroj vygeneruje chybu. MIDL získáte představu, co došlo k chybě, pokud je definován /o (přesměrovat výstup).

Dávkový soubor, jako je například vlastního kroku sestavení nebo události sestavení, který není informativní o podmínky při selhání může být také důvodem této chyby.