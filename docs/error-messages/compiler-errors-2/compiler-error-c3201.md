---
title: Chyba kompilátoru C3201
ms.date: 11/04/2016
f1_keywords:
- C3201
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
ms.openlocfilehash: 4da6616c59ea4b8a720c8e2dc9742e37a9939171
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738762"
---
# <a name="compiler-error-c3201"></a>Chyba kompilátoru C3201

seznam parametrů šablony pro šablonu třídy ' Template ' neodpovídá seznamu parametrů šablony pro parametr šablony ' Template '.

Předali jste šablonu třídy v argumentu šabloně třídy, která nepřijímá parametr šablony, nebo jste předali neshodující počet argumentů šablony pro výchozí argument šablony.

```cpp
// C3201.cpp
template<typename T1, typename T2>
class X1
{
};

template<template<typename T> class U = X1>   // C3201
class X2
{
};

template<template<typename T, typename V> class U = X1>   // OK
class X3
{
};
```
