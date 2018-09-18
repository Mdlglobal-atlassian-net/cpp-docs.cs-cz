---
title: Chyba kompilátoru C2873 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2873
dev_langs:
- C++
helpviewer_keywords:
- C2873
ms.assetid: 7a10036b-400e-4364-bd2f-dcd7370c5e28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf0cc5663d81d6c1e7ad6a9f1a5f7ca167f12909
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049901"
---
# <a name="compiler-error-c2873"></a>Chyba kompilátoru C2873

'symbol': symbol nejde používat v deklarace using

A `using` chybí direktiva [obor názvů](../../cpp/namespaces-cpp.md) – klíčové slovo. To způsobí, že kompilátor interpretuje jako kód [using – deklarace](../../cpp/using-declaration.md) spíše než [direktiva using](../../cpp/namespaces-cpp.md#using_directives).