---
title: Testování pro nalezení chyb extrakce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- extraction errors
ms.assetid: 6a681028-adba-4557-8f7b-f137932905f8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc84277b654a79eebd38461c3ee83aefd533e4a8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853895"
---
# <a name="testing-for-extraction-errors"></a>Testování pro nalezení chyb extrakce

Výstupní chyba zpracování funkce popsané v [chyba zpracování funkce](../standard-library/output-file-stream-member-functions.md), platí pro vstupní datové proudy. Testování pro nalezení chyb při extrakci je důležité. Vezměte v úvahu tento příkaz:

```cpp
cin>> n;
```

Pokud `n` je podepsaná hodnota typu integer, hodnotu větší než 32 767 (maximální povolenou hodnotu, nebo MAX_INT) nastaví datový proud `fail` bit a `cin` objekt nepoužitelný. Všechny následné extrakce za následek okamžitou vrátit se žádná hodnota uložena.

## <a name="see-also"></a>Viz také

[Vstupní streamy](../standard-library/input-streams.md)<br/>
