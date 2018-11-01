---
title: Chyba kompilátoru C2592
ms.date: 11/04/2016
f1_keywords:
- C2592
helpviewer_keywords:
- C2592
ms.assetid: 833a4d7b-66ef-4d4c-ae83-a533c2b0eb07
ms.openlocfilehash: 2ea5919f073f2fd608dca332e721be0669760a0a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50600140"
---
# <a name="compiler-error-c2592"></a>Chyba kompilátoru C2592

'class': "base_class_2" je zděděno od "base_class_1" a nejde znova specifikovat

Můžete nastavit jenom základní třídy, které nejsou odvozeny z jiných základních tříd. V takovém případě pouze `base_class_1` je potřeba ve specifikaci `class` protože `base_class_1` již dědí `base_class_2`.