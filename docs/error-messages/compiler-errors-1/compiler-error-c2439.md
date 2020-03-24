---
title: Chyba kompilátoru C2439
ms.date: 11/04/2016
f1_keywords:
- C2439
helpviewer_keywords:
- C2439
ms.assetid: 3c5dbe5c-b7d3-4bb0-8619-92f6e280461e
ms.openlocfilehash: 99f3644869f6c5395684643f0e7802f3a01baa62
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80205358"
---
# <a name="compiler-error-c2439"></a>Chyba kompilátoru C2439

' identifier ': člen nelze inicializovat

Člena třídy, struktury nebo sjednocení nelze inicializovat.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. Pokus o inicializaci nepřímé základní třídy nebo struktury.

1. Pokus o inicializaci zděděného člena třídy nebo struktury. Zděděný člen musí být inicializován konstruktorem třídy nebo struktury.
