---
title: Upozornění kompilátoru (úroveň 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c9bf60e8eec0ee6416bda3323583f3e056fce1a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174879"
---
# <a name="compiler-warning-level-1-c4819"></a>Upozornění kompilátoru (úroveň 1) C4819

> Soubor obsahuje znak, který nemůže být reprezentovaný v aktuální znakové stránce (*číslo*). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.

K C4819 dochází při kompilaci zdrojového souboru ANSI v systému pomocí znakové sady, která nemůže reprezentovat všechny znaky v souboru.

Existuje několik způsobů, jak C4819 vyřešit. Jedním z jednoduchých způsobů je odstranit problematický znak, pokud ho nepotřebujete, například pokud je v komentáři. Můžete nastavit systémovou znakovou stránku v Ovládacích panelech na jednu, která podporuje znakovou sadu, kterou používá váš zdrojový kód. [Řídicí sekvence](/cpp/c-language/escape-sequences) Unicode lze použít k vytvoření znaků nebo řetězců, které ve zdrojovém kódu používají pouze základní znakovou sadu ANSI. Nakonec můžete soubor uložit ve formátu Unicode s podpisem, označovaný také jako znak pořadí bajtů (BOM).

Pokud chcete soubor uložit ve formátu Unicode, v sadě Visual Studio vyberte **soubor** > **Uložit jako**. V dialogovém okně **Uložit soubor jako** vyberte v rozevíracím seznamu tlačítko **Uložit** a zvolte možnost **Uložit s kódováním**. Pokud uložíte do stejného názvu souboru, budete možná muset potvrdit, že chcete soubor nahradit. V dialogovém okně **Upřesnit možnosti uložení** zvolte kódování, které může představovat všechny znaky v souboru – například **Unicode (UTF-8 s podpisem)-codepage 65001**– a pak zvolte **OK**.
