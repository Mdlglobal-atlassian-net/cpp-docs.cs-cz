---
title: Chyba kompilátoru C3728
ms.date: 11/04/2016
f1_keywords:
- C3728
helpviewer_keywords:
- C3728
ms.assetid: 6b510cb1-887f-4fcd-9a1f-3bb720417ed1
ms.openlocfilehash: 8aec3ae1ff629ef7fa000182cde29e306a471315
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165871"
---
# <a name="compiler-error-c3728"></a>Chyba kompilátoru C3728

' Event ': událost nemá metodu vyvolání

Metadata vytvořená pomocí jazyka, například C#, který neumožňuje vyvolání události mimo třídu, ve které byla definována, byla zahrnuta v direktivě [#using](../../preprocessor/hash-using-directive-cpp.md) a vizuální C++ program používající programování CLR se pokusil vyvolat událost.

Chcete-li vyvolat událost v programu vyvinutém v jazyce C#, jako je, třída obsahující událost musí také definovat veřejnou metodu, která vyvolává událost.
