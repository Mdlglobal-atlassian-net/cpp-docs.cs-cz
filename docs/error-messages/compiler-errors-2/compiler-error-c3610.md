---
title: Chyba kompilátoru C3610
ms.date: 11/04/2016
f1_keywords:
- C3610
helpviewer_keywords:
- C3610
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
ms.openlocfilehash: 9965e6420171b2ea48c8fb7bacc0a5a37ea2f227
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344608"
---
# <a name="compiler-error-c3610"></a>Chyba kompilátoru C3610

'valuetype': typ hodnoty musí být typu boxed, může být volána metoda "method"

Ve výchozím nastavení není typu hodnoty na spravované haldě. Než bude možné volat metody, jako z .NET runtime třídy `Object`, budete muset přesunout typ hodnoty na spravované haldě.

C3610 dosažitelný pouze pomocí možnosti kompilátoru zastaralé **oldSyntax**.
