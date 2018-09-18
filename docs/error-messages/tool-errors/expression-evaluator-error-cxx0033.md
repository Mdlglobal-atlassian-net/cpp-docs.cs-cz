---
title: Vyhodnocování výrazu CXX0033 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0033
dev_langs:
- C++
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04f37b53c30d36a43d339132bfd9baca3e5ec70c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46057194"
---
# <a name="expression-evaluator-error-cxx0033"></a>Chyba při vyhodnocování výrazu CXX0033

Chyba v omf – informace o typu

Spustitelný soubor nemá formát modulu platný objekt (omf –) pro ladění.

Tato chyba se shoduje s CAN0033.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. Spustitelný soubor nebyl vytvořen pomocí linkeru vydané s touto verzí sady Visual C++. Znovu propojit objektový kód v aktuální verzi LINK.exe.

1. Tento soubor .exe je poškozený. Znovu zkompilovat a znovu propojit do programu.