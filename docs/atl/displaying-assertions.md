---
title: Zobrazení kontrolních výrazů
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: bb06b8f124180ed566ecf2c761deb359444fb019
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289985"
---
# <a name="displaying-assertions"></a>Zobrazení kontrolních výrazů

Pokud klient připojený k vaší službě se zobrazí přestane reagovat, může služba posuzovat a zobrazí okno se zprávou, která se vám nedaří zobrazit. Můžete to ověřit pomocí ladicího programu Visual C++ na ladění vašeho kódu (viz [pomocí Správce úloh](../atl/using-task-manager.md) výše v této části).

Pokud zjistíte, že vaše služba se zobrazuje okno se zprávou, která nelze zobrazit, můžete nastavit **povolit službu interakcí s plochou** možnost před použitím služby znovu. Tato možnost je parametr spuštění, která umožňuje všechny okna se zprávou zobrazí ve službě a zobrazí v klientských počítačích. Nastavení této možnosti, otevřete aplikaci ovládacím panelu služby, vyberte službu, klikněte na tlačítko **spuštění**a pak vyberte **povolit službu interakcí s plochou** možnost.

## <a name="see-also"></a>Viz také:

[Tipy pro ladění](../atl/debugging-tips.md)
