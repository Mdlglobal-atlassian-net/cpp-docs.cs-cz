---
title: Chyba příkazového řádku D8045 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D8045
dev_langs:
- C++
helpviewer_keywords:
- D8045
ms.assetid: 01c8808c-bac1-4b4d-8a90-b595f95e9318
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6838202178e8012df61d17e2434461d6f4858bf3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022783"
---
# <a name="command-line-error-d8045"></a>Chyba příkazového řádku D8045

Soubor C 'file' s možností/CLR nelze zkompilovat.

Mohou být předány pouze soubory zdrojového kódu C++ kompilaci, která používá **/CLR**.  Použití **/TP** ke kompilaci souboru .c jako souboru s příponou .cpp, naleznete v tématu [/Tc /Tp /TC, /TP (určení typu zdrojového souboru)](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md) Další informace.

Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).

D8045 může také dojít, pokud kompilujete aplikace ATL s použitím Visual C++. Zobrazit [postupy: přechod na/CLR](../../dotnet/how-to-migrate-to-clr.md) Další informace.