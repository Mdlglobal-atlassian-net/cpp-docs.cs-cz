---
title: Závažná chyba C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: ba2b797c9bf521533e7c2ccff8d358b6216d392f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266463"
---
# <a name="fatal-error-c1311"></a>Závažná chyba C1311

Formát COFF nemůže staticky inicializovat 'var' se číslo b adresy.

Adresa, jehož hodnota není známá v době kompilace nelze přiřadit staticky proměnnou, jejíž typ má úložiště méně než čtyři bajty.

Této chybě může dojít v kódu, který je jinak platný C++.

Následující příklad ukazuje jednu podmínku, která může způsobit, že C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```