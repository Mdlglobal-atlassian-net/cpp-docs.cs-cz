---
title: Řešení nejednoznačných deklarací (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 3d773ee7-bbea-47de-80c2-cb0a9d4ec0b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3dc5b5a2b7d8add493efc144931160afb7d15020
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467509"
---
# <a name="resolving-ambiguous-declarations-c"></a>Řešení nejednoznačných deklarací (C++)
Chcete-li provést explicitní převody z jednoho typu na jiný, je zapotřebí použít přetypování a určit název požadovaného typu. Některá přetypování způsobují nejednoznačnost syntaxe. Následující přetypování podobné funkci je nejednoznačné:  
  
```cpp 
char *aName( String( s ) );  
```  
  
 Není jasné, zda se jedná o deklaraci funkce nebo objektu s přetypovat jako inicializátor function-style: může jít o deklaraci funkce vracející typ `char *` , která přijímá jeden argument typu `String`, nebo může jít o deklaraci objektu `aName` a provést jeho inicializaci hodnotou `s` přetypování na typ `String`.  
  
 Může-li být deklarace považována za platnou deklaraci funkce, je jako deklarace funkce zpracována. Pouze v případě, že o deklaraci funkce jít nemůže – tedy pokud by byla syntaxe chybná – je příkaz zkoumán, zda jde o přetypování podobné funkci. Proto kompilátor považuje příkaz za deklaraci funkce a ignoruje závorky okolo identifikátoru `s`. Na druhou stranu, příkazy:  
  
```cpp 
char *aName( (String)s );  
```  
  
 and  
  
```cpp 
char *aName = String( s );  
```  
  
 jsou jednoznačnou deklarací objektů a uživatelsky definovaný převod z typu `String` na typ `char *` se vyvolá k inicializaci objektu `aName`.  