---
title: Závažná chyba C1055
ms.date: 11/04/2016
f1_keywords:
- C1055
helpviewer_keywords:
- C1055
ms.assetid: a9fb9190-d7eb-4d5f-b1a2-a41e584a28c1
ms.openlocfilehash: e6df4870d7af49c369be7e513791955599c48326
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390643"
---
# <a name="fatal-error-c1055"></a>Závažná chyba C1055

limit kompilátoru: došly klíče

Zdrojový soubor obsahuje příliš mnoho symbolů. Kompilátor nemá dostatek klíčů hash pro symbol tabulku.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Chcete-li vyřešit pomocí následujících možná řešení

1. Zdrojový soubor rozdělte na menší soubory.

1. Odstranění nepotřebných hlavičkové soubory.

1. Znovu použít dočasný a globální proměnné místo vytvoření nové značky.