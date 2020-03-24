---
title: Závažná chyba C1311
ms.date: 11/04/2016
f1_keywords:
- C1311
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
ms.openlocfilehash: e57e4e0899a5f9d81e87a203b1b699cef0884f0d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203265"
---
# <a name="fatal-error-c1311"></a>Závažná chyba C1311

Formát COFF nemůže staticky inicializovat var s počtem bajtů adresy.

Adresa, jejíž hodnota není známa v době kompilace, nemůže být staticky přiřazena proměnné, jejíž typ má úložiště menší než čtyři bajty.

K této chybě může dojít v kódu, který je C++jinak platný.

Následující příklad ukazuje jednu podmínku, která může způsobit C1311.

```
char c = (char)"Hello, world";   // C1311
char *d = (char*)"Hello, world";   // OK
```
