---
title: Hodnota Null, Statement (C) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- semicolon, C null statement
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f505c926370bfbee98bf28970ee78d3152feb025
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="null-statement-c"></a>Null – příkaz (C)
„Příkaz null“ je příkaz obsahující pouze středník. Může se objevit všude, kde se očekává příkaz. Když je příkaz null vykonáván, nic se nestane. Správným způsobem zápisu příkazu null je:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
;  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Příkazy, jako **provést**, **pro**, **Pokud**, a `while` vyžadují, aby spustitelného souboru příkazu zobrazí jako text příkazu. Příkaz null splňuje požadavek syntaxe v případech, které nepotřebují důležité tělo příkazu.  
  
 Stejně jako u jiných příkazů jazyka C lze před příkaz null umístit popisek. Chcete-li položce, která není příkazem, například složené závorce složeného příkazu, dát popisek, lze příkaz null popsat a vložit jej těsně před položku, čímž docílíte stejného efektu.  
  
 Následující příklad znázorňuje příkaz null:  
  
```  
for ( i = 0; i < 10; line[i++] = 0 )  
     ;  
```  
  
 V tomto příkladu výraz smyčky **pro** příkaz `line[i++] = 0` inicializuje prvních 10 elementy `line` na hodnotu 0. Tělo příkazu je příkaz null, protože žádné další příkazy nejsou nezbytné.  
  
## <a name="see-also"></a>Viz také  
 [Příkazy](../c-language/statements-c.md)