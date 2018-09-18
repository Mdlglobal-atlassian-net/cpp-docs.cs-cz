---
title: Chyba kompilátoru C2567 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2567
dev_langs:
- C++
helpviewer_keywords:
- C2567
ms.assetid: 9c140ac9-7059-47e6-9ba1-e7939c8c0dc3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb09aacc1b81e9f0e0c9c96a496eccc89a061f37
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46104231"
---
# <a name="compiler-error-c2567"></a>Chyba kompilátoru C2567

nejde otevřít metadata v: 'file', soubor může mít byly odstraněny nebo přesunuty

Soubor metadat, která byla popsána ve zdroji (s `#using`) nebyl nalezen ve stejném adresáři v procesu kompilátoru back-end jako byl proces front-endu kompilátoru. Zobrazit [# direktiva using](../../preprocessor/hash-using-directive-cpp.md) Další informace.

C2567 může nastat, pokud kompilujete s **/c** na jednom počítači a pokusíte se generování kódu při propojování na jiném počítači. Další informace najdete v tématu [parametru/LTCG (generování kódu při propojování odkaz)](../../build/reference/ltcg-link-time-code-generation.md)).

Může také znamenat, že váš počítač měl žádná další paměť.

Chcete-li tuto chybu opravit, ujistěte se, že je ve stejném umístění adresáře souboru metadat pro všechny fáze procesu sestavení.