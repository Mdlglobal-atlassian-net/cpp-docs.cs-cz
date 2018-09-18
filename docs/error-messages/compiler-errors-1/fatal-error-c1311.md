---
title: Závažná chyba C1311 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1311
dev_langs:
- C++
helpviewer_keywords:
- C1311
ms.assetid: 6590a06c-ce9d-4f17-8f62-c809343143b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d93aa28d0cef3c07fd469349d485c4009fa4771d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091059"
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