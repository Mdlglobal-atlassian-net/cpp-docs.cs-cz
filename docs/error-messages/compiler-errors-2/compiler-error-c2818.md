---
title: Chyba kompilátoru C2818
ms.date: 11/04/2016
f1_keywords:
- C2818
helpviewer_keywords:
- C2818
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
ms.openlocfilehash: f6e33d0e0ee139138df7d8e11357100b3ec3a1a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388693"
---
# <a name="compiler-error-c2818"></a>Chyba kompilátoru C2818

použití přetíženého operátoru operator ->' je rekurzivní prostřednictvím typu 'type'

Předefinování operátor přístupu členů třídy obsahuje rekurzivního `return` příkazu. K předefinování `->` operátor s rekurze, je nutné přesunout rutina rekurzivní do samostatné funkce volána z operátoru přepsat funkci.