---
title: Chyba sestavení projektu PRJ0035
ms.date: 08/27/2018
f1_keywords:
- PRJ0035
helpviewer_keywords:
- PRJ0035
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
ms.openlocfilehash: 8486c4f62f637f6f7e9826a289c21f8f194eb9f3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192169"
---
# <a name="project-build-error-prj0035"></a>Chyba sestavení projektu PRJ0035

> Soubor XML '*File*' obsahuje obsah v kódování Unicode, který nelze přeložit na znakovou stránku ANSI uživatele.
>
> *Obsah UNICODE souboru*

*soubor* je soubor XML vytvořený jako příkazový řádek pro nástroj pro nasazení webu.

Systém projektu našel v některé vlastnosti na stránce vlastností nasazení webu znaky Unicode, které se nedají správně přeložit do ANSI.

Řešením této chyby je aktualizovat obsah vlastnosti tak, aby používal ANSI nebo nainstalovat znakovou stránku do počítače a nastavit ji jako výchozí systém.
