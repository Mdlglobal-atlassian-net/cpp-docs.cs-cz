---
title: Zobrazení kontrolních výrazů
ms.date: 05/05/2019
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: 962a33a7d5d922f7f1655e22b2c9d0acdcf8925c
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221262"
---
# <a name="displaying-assertions"></a>Zobrazení kontrolních výrazů

Pokud klient připojený k vaší službě se zobrazí přestane reagovat, může služba posuzovat a zobrazí okno se zprávou, která se vám nedaří zobrazit. Můžete to ověřit pomocí ladicího programu sady Visual Studio na ladění vašeho kódu (viz [pomocí Správce úloh](../atl/using-task-manager.md) výše v této části).

Pokud zjistíte, že vaše služba se zobrazuje okno se zprávou, která nelze zobrazit, můžete nastavit **povolit službu interakcí s plochou** možnost před použitím služby znovu. Tato možnost je parametr spuštění, která umožňuje všechny okna se zprávou zobrazí ve službě a zobrazí v klientských počítačích. Nastavení této možnosti, otevřete aplikaci ovládacím panelu služby, vyberte službu, klikněte na tlačítko **spuštění**a pak vyberte **povolit službu interakcí s plochou** možnost.

## <a name="see-also"></a>Viz také:

[Tipy pro ladění](../atl/debugging-tips.md)
