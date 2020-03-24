---
title: Chyba kompilátoru C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: 00952e55f1b732bd9af3733f5c0ec575a39116fe
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202105"
---
# <a name="compiler-error-c2818"></a>Chyba kompilátoru C2818

použití přetíženého operátoru operator-> je rekurzivní prostřednictvím typu Type.

Předefinování operátoru přístupu člena třídy obsahuje rekurzivní příkaz `return`. Chcete-li předefinovat operátor `->` pomocí rekurze, je nutné přesunout rekurzivní rutinu do samostatné funkce volané z funkce override operátor.
