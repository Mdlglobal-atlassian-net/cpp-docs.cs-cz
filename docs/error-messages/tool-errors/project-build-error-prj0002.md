---
title: Chyba sestavení projektu PRJ0002
ms.date: 08/27/2018
f1_keywords:
- PRJ0002
helpviewer_keywords:
- PRJ0002
ms.assetid: 1c820b1f-9a24-4681-80ed-4fcbfd7caa00
ms.openlocfilehash: d8e13bcc03a02fd9dbc739566a92025a7b97d598
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359706"
---
# <a name="project-build-error-prj0002"></a>Chyba sestavení projektu PRJ0002

> Chyba výsledek vrácený z "*příkazového řádku*".

V příkazu *příkazového řádku*, který byl vytvořen ze vstupu uživatele v **stránky vlastností** zobrazí se v dialogovém okně vrátil kód chyby, ale žádné informace o **výstup** okna .

Řešení této chyby závisí na který nástroj vygeneruje chybu. MIDL získáte představu, co došlo k chybě, pokud je definován /o (přesměrovat výstup).

Dávkový soubor, jako je například vlastního kroku sestavení nebo události sestavení, který není informativní o podmínky při selhání může být také důvodem této chyby.