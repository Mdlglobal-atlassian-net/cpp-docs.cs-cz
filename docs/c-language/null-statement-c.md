---
title: Null – příkaz (C)
ms.date: 11/04/2016
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
ms.openlocfilehash: bee044049ed14796a97edc62bbb180ab19700564
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503048"
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