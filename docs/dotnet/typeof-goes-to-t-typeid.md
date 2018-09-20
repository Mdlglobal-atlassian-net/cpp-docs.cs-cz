---
title: typeof přechází na T::typeid | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- typeid operator
- __typeof keyword
- typeid keyword [C++]
ms.assetid: 6a0d35a7-7a1a-4070-b187-cff37cfdc205
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 4433061fceef455685b6588c81c8c2e434253433
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374670"
---
# <a name="typeof-goes-to-ttypeid"></a>typeof přechází na T::typeid

`typeof` Operátor použitý ve spravovaných rozšíření pro C++ byl nahrazen `typeid` – klíčové slovo v jazyce Visual C++.

Ve spravovaných rozšíření `__typeof()` operátor vrátí přidružený `Type*` objektu po uplynutí název spravovaného typu. Příklad:

```
// Creates and initializes a new Array instance.
Array* myIntArray =
   Array::CreateInstance( __typeof(Int32), 5 );
```

V nové syntaxi `__typeof` byla nahrazena další formu `typeid` , která vrací `Type^` Pokud je zadaný spravovaným typem.

```
// Creates and initializes a new Array instance.
Array^ myIntArray =
   Array::CreateInstance( Int32::typeid, 5 );
```

## <a name="see-also"></a>Viz také

[Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)<br/>
[identifikátor TypeId.](../windows/typeid-cpp-component-extensions.md)