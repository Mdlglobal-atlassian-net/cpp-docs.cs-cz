---
title: Závažná chyba C1081 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1081
dev_langs:
- C++
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b34f2f19a0bb8770ea9292fef120c415c0fb255a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060524"
---
# <a name="fatal-error-c1081"></a>Závažná chyba C1081

'symbol': název souboru je příliš dlouhý

Délka cesty souboru přesahuje `_MAX_PATH` (definované STDLIB.h jako 260 znaků). Zkraťte název souboru.

Při volání CL.exe s krátký název souboru, kompilátor bude pravděpodobně nutné generovat úplnou cestu. Například `cl -c myfile.cpp` může způsobit, že kompilátor vygeneroval:

```
D:\<very-long-directory-path>\myfile.cpp
```