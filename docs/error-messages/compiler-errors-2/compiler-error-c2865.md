---
title: Chyba kompilátoru C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: dd4374c1a577c4c39c5dec107ed5025d7cdc79c2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201693"
---
# <a name="compiler-error-c2865"></a>Chyba kompilátoru C2865

' function ': neplatné porovnání pro handle_or_pointer

Můžete porovnat odkazy na [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md) nebo spravované typy odkazů pouze pro rovnost, aby viděli, zda odkazují na stejný objekt (= =) nebo na různé objekty (! =).

Nemůžete je porovnat pro řazení, protože modul runtime .NET může kdykoli přesunout spravované objekty a změnit výsledek testu.
