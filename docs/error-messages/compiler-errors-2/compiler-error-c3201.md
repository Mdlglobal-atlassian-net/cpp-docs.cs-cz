---
title: Chyba kompilátoru C3201 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3201
dev_langs:
- C++
helpviewer_keywords:
- C3201
ms.assetid: ec19cd64-1789-40a3-b2db-dff2852b9d98
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 466899de89e1f8760ec78e7d346ef949fab667be
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074250"
---
# <a name="compiler-error-c3201"></a>Chyba kompilátoru C3201

Seznam parametrů šablony pro šablonu tříd 'template' neodpovídá seznamu parametrů šablony pro parametr šablony "template.

Byl předán šablony třídy v argumentu šablony třídy, který nepřijímá parametr šablony, nebo jste předali neodpovídající počet argumentů šablony pro výchozí argument šablony.

```
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