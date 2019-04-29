---
title: Kompilátor upozornění (úroveň 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: d43b49d473e7113d8cdfb89aaa6e93045e13d0f7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406311"
---
# <a name="compiler-warning-level-1-c4819"></a>Kompilátor upozornění (úroveň 1) C4819

> Tento soubor obsahuje znak, který nemůže být reprezentovaný v aktuální znakové stránce (*číslo*). Uložte soubor ve formátu Unicode, aby se zabránilo ztrátě dat.

C4819 vyvolá při kompilaci zdrojového souboru ANSI v systému pomocí znakové stránky, která nemůže představovat všechny znaky v souboru.

Chcete-li vyřešit C4819 několika způsoby. Jednoduše je odebrat problematické znaky, pokud ho nepotřebujete, například, pokud je v komentáři. Systémové znakové stránky můžete nastavit v Ovládacích panelech na takový, který podporuje znakovou sadu použitou ve zdrojovém kódu. Můžete použít Unicode [řídicí sekvence](/cpp/c-language/escape-sequences) vytvořit znaků nebo řetězce, které používají pouze základní ANSI znaková sada ve zdrojovém kódu. Nakonec můžete uložit soubor ve formátu Unicode s podpisem, označované také jako značku pořadí bajtů (BOM).

Chcete-li uložit soubor ve formátu Unicode, v sadě Visual Studio, zvolte **souboru** > **uložit jako**. V **uložit soubor jako** dialogového okna, vyberte v rozevíracím seznamu na **Uložit** tlačítko a zvolte **uložit s kódováním**. Pokud uložíte na stejný název souboru, budete muset potvrdit, že chcete nahradit soubor. V **pokročilé nastavení uložení** dialogovém okně vybrat kódování, které mohou představovat všechny znaky v souboru – například **kódování Unicode (UTF-8 s podpisem) - znaková stránka 65001**– a klikněte na tlačítko  **OK**.