---
title: Řešení nejednoznačných deklarace (C++) | Microsoft Docs
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
ms.openlocfilehash: 530111ee439a991201debab876d485a36b7f5ac5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="resolving-ambiguous-declarations-c"></a>Řešení nejednoznačných deklarace (C++)
Chcete-li provést explicitní převody z jednoho typu na jiný, je zapotřebí použít přetypování a určit název požadovaného typu. Některá přetypování způsobují nejednoznačnost syntaxe. Následující přetypování podobné funkci je nejednoznačné:  
  
```  
char *aName( String( s ) );  
```  
  
 Je jasné, jestli je funkce deklaraci nebo deklarace objektu pomocí funkce stylu přetypovat jako inicializátoru: ho může deklarovat funkci vrácení typ **char \***  , která má jeden argument typu `String` , nebo se může deklarovat objekt `aName` a provést jeho inicializaci s hodnotou `s` přetypování na typ `String`.  
  
 Může-li být deklarace považována za platnou deklaraci funkce, je jako deklarace funkce zpracována. Pouze v případě, že o deklaraci funkce jít nemůže – tedy pokud by byla syntaxe chybná – je příkaz zkoumán, zda jde o přetypování podobné funkci. Proto kompilátor považuje příkaz za deklaraci funkce a ignoruje závorky okolo identifikátoru `s`. Na druhou stranu, příkazy:  
  
```  
char *aName( (String)s );  
```  
  
 and  
  
```  
char *aName = String( s );  
```  
  
 jsou jasně deklarace objektů a uživatelem definovaný převod z typu `String` na typ **char \***  je volána k provedení inicializace `aName`.  
  
## <a name="see-also"></a>Viz také  
 