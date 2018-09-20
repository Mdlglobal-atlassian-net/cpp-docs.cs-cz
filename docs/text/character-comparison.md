---
title: Porovnání znaků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- comparing characters
- MBCS [C++], character comparison
- characters [C++], comparing
ms.assetid: 18846e44-3e6e-40c4-9b42-3153fb15db20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c3412939bac9dace6f3abaacda75ed73d6e60f21
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46428067"
---
# <a name="character-comparison"></a>Porovnávání znaků

Použijte následující tipy:

- Porovnání známé vedoucí bajt s znaku ASCII funguje správně:

    ```cpp
    if( *sz1 == 'A' )
    ```

- Porovnání dvou znaků Neznámý vyžaduje použití některého z makra definovaná v Mbstring.h:

    ```cpp
    if( !_mbccmp( sz1, sz2) )
    ```

   Tím se zajistí, že jsou oba bajtů dvoubajtové znakové porovnána shoda.

## <a name="see-also"></a>Viz také

[MBCS – tipy pro programování](../text/mbcs-programming-tips.md)<br/>
[Přetečení vyrovnávací paměti](../text/buffer-overflow.md)