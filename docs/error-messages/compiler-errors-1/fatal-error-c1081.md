---
title: Závažná chyba C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: f3c9f9bde5da7fb120accbb9a8d72e5715ab9d2b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50569670"
---
# <a name="fatal-error-c1081"></a>Závažná chyba C1081

'symbol': název souboru je příliš dlouhý

Délka cesty souboru přesahuje `_MAX_PATH` (definované STDLIB.h jako 260 znaků). Zkraťte název souboru.

Při volání CL.exe s krátký název souboru, kompilátor bude pravděpodobně nutné generovat úplnou cestu. Například `cl -c myfile.cpp` může způsobit, že kompilátor vygeneroval:

```
D:\<very-long-directory-path>\myfile.cpp
```