---
title: Hodnota Null, Statement (C) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4428852dd3b949bea75961d3878fc23d27a2b4f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46106275"
---
# <a name="null-statement-c"></a>Null – příkaz (C)

„Příkaz null“ je příkaz obsahující pouze středník. Může se objevit všude, kde se očekává příkaz. Když je příkaz null vykonáván, nic se nestane. Správným způsobem zápisu příkazu null je:

## <a name="syntax"></a>Syntaxe

> **;**

## <a name="remarks"></a>Poznámky

Příkazy, jako **proveďte**, **pro**, **Pokud**, a `while` vyžadují, aby byl spustitelný příkaz zobrazí jako těla příkazu. Příkaz null splňuje požadavek syntaxe v případech, které nepotřebují důležité tělo příkazu.

Stejně jako u jiných příkazů jazyka C lze před příkaz null umístit popisek. Chcete-li položce, která není příkazem, například složené závorce složeného příkazu, dát popisek, lze příkaz null popsat a vložit jej těsně před položku, čímž docílíte stejného efektu.

Následující příklad znázorňuje příkaz null:

```C
for ( i = 0; i < 10; line[i++] = 0 )
     ;
```

V tomto příkladu výraz smyčky **pro** příkaz `line[i++] = 0` inicializuje prvních 10 prvků pole `line` na hodnotu 0. Tělo příkazu je příkaz null, protože žádné další příkazy nejsou nezbytné.

## <a name="see-also"></a>Viz také

[Příkazy](../c-language/statements-c.md)