---
title: Zobrazení kontrolních výrazů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ff7b9b29808e310be2d5568add64a0294bc67e7
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43762379"
---
# <a name="displaying-assertions"></a>Zobrazení kontrolních výrazů

Pokud klient připojený k vaší službě se zobrazí přestane reagovat, může služba posuzovat a zobrazí okno se zprávou, která se vám nedaří zobrazit. Můžete to ověřit pomocí ladicího programu Visual C++ na ladění vašeho kódu (viz [pomocí Správce úloh](../atl/using-task-manager.md) výše v této části).

Pokud zjistíte, že vaše služba se zobrazuje okno se zprávou, která nelze zobrazit, můžete nastavit **povolit službu interakcí s plochou** možnost před použitím služby znovu. Tato možnost je parametr spuštění, která umožňuje všechny okna se zprávou zobrazí ve službě a zobrazí v klientských počítačích. Nastavení této možnosti, otevřete aplikaci ovládacím panelu služby, vyberte službu, klikněte na tlačítko **spuštění**a pak vyberte **povolit službu interakcí s plochou** možnost.

## <a name="see-also"></a>Viz také

[Tipy pro ladění](../atl/debugging-tips.md)

