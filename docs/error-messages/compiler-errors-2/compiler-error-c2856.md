---
title: Compiler Error C2856
ms.date: 11/04/2016
f1_keywords:
- C2856
helpviewer_keywords:
- C2856
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
ms.openlocfilehash: 1e515f250c8ab9d1008ded91b99176f1d86d7cd1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406844"
---
# <a name="compiler-error-c2856"></a>Compiler Error C2856

\#hdrstop – Direktiva pragma nemůže být uvnitř bloku #if.

`hdrstop` – Direktiva pragma nelze umístit uvnitř těla bloku podmíněné kompilace.

Přesunout `#pragma hdrstop` příkazu, který není obsažen v oblasti `#if/#endif` bloku.