---
title: Chyba při vyhodnocování výrazu CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 8563eb2fbc24c6ad8db639d2e227802412a16090
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397052"
---
# <a name="expression-evaluator-error-cxx0033"></a>Chyba při vyhodnocování výrazu CXX0033

Chyba v omf – informace o typu

Spustitelný soubor nemá formát modulu platný objekt (omf –) pro ladění.

Tato chyba se shoduje s CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Spustitelný soubor nebyl vytvořen pomocí linkeru vydané s touto verzí sady Visual C++. Znovu propojit objektový kód v aktuální verzi LINK.exe.

1. Tento soubor .exe je poškozený. Znovu zkompilovat a znovu propojit do programu.