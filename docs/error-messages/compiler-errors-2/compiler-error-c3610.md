---
title: Chyba kompilátoru C3610 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3610
dev_langs:
- C++
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b46b3669978ff3735d5a16015ca0a01e65f07ae9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037850"
---
# <a name="compiler-error-c3610"></a>Chyba kompilátoru C3610

'valuetype': typ hodnoty musí být typu boxed, může být volána metoda "method"

Ve výchozím nastavení není typu hodnoty na spravované haldě. Než bude možné volat metody, jako z .NET runtime třídy `Object`, budete muset přesunout typ hodnoty na spravované haldě.

C3610 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**.
