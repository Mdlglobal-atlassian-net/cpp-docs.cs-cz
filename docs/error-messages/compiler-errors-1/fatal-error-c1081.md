---
title: Závažná chyba C1081
ms.date: 11/04/2016
f1_keywords:
- C1081
helpviewer_keywords:
- C1081
ms.assetid: e58adf17-cbe1-4955-a5c7-80622bbba249
ms.openlocfilehash: b8630a26d14c68a5f1abe45bb0b8d0141d0dedbb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80204188"
---
# <a name="fatal-error-c1081"></a>Závažná chyba C1081

' symbol ': název souboru je příliš dlouhý.

Délka cesty k souboru přesahuje `_MAX_PATH` (definováno STDLIB. h jako 260 znaků). Zkraťte název souboru.

Pokud zavoláte CL. exe se stručným názvem souboru, kompilátor bude muset vygenerovat úplnou cestu. Například `cl -c myfile.cpp` může způsobit vygenerování kompilátorem:

```
D:\<very-long-directory-path>\myfile.cpp
```
