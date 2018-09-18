---
title: Závažná chyba kompilátoru prostředků RC1018 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RC1018
dev_langs:
- C++
helpviewer_keywords:
- RC1018
ms.assetid: bb1d2efd-6898-412f-bb03-9ff94c54e4dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2c4fa0a9964c3faeed010b82f8cd98f2782fb1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46028503"
---
# <a name="resource-compiler-fatal-error-rc1018"></a>Závažná chyba kompilátoru prostředků RC1018

neočekávané "#elif.

`#elif` Směrnice nenacházely se v rámci `#if`, **#ifdef**, nebo **#ifndef** vytvořit.

Ujistěte se, že dochází `#if`, **#ifdef**, nebo **#ifndef** v platnosti než tento příkaz.