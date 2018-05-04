---
title: Registrátor ATL a Backus Nauer formuláři syntaxe (BNF) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- BNF notation
- Backus Nauer Form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4137dd94886456d5813076f3cb328bac5ecf5c03
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="understanding-backus-nauer-form-bnf-syntax"></a>Principy Backus Nauer formuláře (BNF) syntaxe
Skripty používané Registrátor ATL jsou popsané v tomto tématu pomocí syntaxe BNF, který používá zápis uvedené v následující tabulce.  
  
|Konvence nebo symbol|Význam|  
|------------------------|-------------|  
|`::=`|Ekvivalent|  
|`&#124;`|NEBO|  
|`X+`|Jeden nebo více `X`s.|  
|`[X]`|`X` je volitelný. Volitelné oddělovače jsou rozlišeny pomocí `[]`.|  
|Všechny **tučné** textu|Řetězcový literál.|  
|Všechny *kurzívou* textu|Postup vytvoření řetězcový literál.|  
  
 Jak je uvedeno v předchozí tabulce, skripty registrátora používat řetězcové literály. Tyto hodnoty jsou skutečný text, který musí být ve vašem skriptu. Následující tabulka popisuje textové literály použít ve skriptu Registrátor ATL.  
  
|Řetězcový literál|Akce|  
|--------------------|------------|  
|**ForceRemove**|Úplně odebere Další klíč (pokud existuje) a pak znovu vytvoří.|  
|**NoRemove**|Během Unregister neodebere Další klíč.|  
|**Val**|Určuje, že `<Key Name>` je ve skutečnosti pojmenované hodnotě.|  
|**Odstranit**|Odstraní Další klíč během registrace.|  
|**s**|Určuje, že další hodnota je řetězec (**REG_SZ**).|  
|**d**|Určuje, že je další hodnotu **DWORD** (**REG_DWORD**).|  
|**m**|Určuje, že další hodnotu multistring (**REG_MULTI_SZ**).|  
|**b**|Určuje, že další hodnotu je binární hodnotu (**REG_BINARY**).|  
  
## <a name="bnf-syntax-examples"></a>Příklady syntaxe BNF  
 Tady je několik příkladů syntaxe vám pomohou pochopit, jak fungují literály zápis a řetězec Registrátor ATL skriptu.  
  
### <a name="syntax-example-1"></a>Příklad syntaxe 1  
  
```  
<registry expression> ::= <Add Key>  
```  
  
 Určuje, že `registry expression` je ekvivalentní `Add Key`.  
  
### <a name="syntax-example-2"></a>Příklad syntaxe 2  
  
```  
<registry expression> ::= <Add Key> | <Delete Key>  
```  
  
 Určuje, že `registry expression` odpovídá buď `Add Key` nebo `Delete Key`.  
  
### <a name="syntax-example-3"></a>Příklad syntaxe 3  
  
```  
<Key Name> ::= '<AlphaNumeric>+'  
```  
  
 Určuje, že `Key Name` je ekvivalentní minimálně jeden `AlphaNumerics`.  
  
### <a name="syntax-example-4"></a>Příklad syntaxe 4  
  
```  
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>  
```  
  
 Určuje, že `Add Key` je ekvivalentní `Key Name`a že textové literály `ForceRemove`, `NoRemove`, a `val`, jsou volitelné.  
  
### <a name="syntax-example-5"></a>Příklad syntaxe 5  
  
```  
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0  
```  
  
 Určuje, že `AlphaNumeric` je ekvivalentní k jakékoli jiné – znak hodnoty NULL.  
  
### <a name="syntax-example-6"></a>Příklad syntaxe 6  
  
```  
val 'testmulti' = m 'String 1\0String 2\0'  
```  
  
 Určuje, že název klíče `testmulti` je nahrazován hodnotu složenou ze `String 1` a `String 2`.  
  
### <a name="syntax-example-7"></a>Příklad syntaxe 7  
  
```  
val 'testhex' = d '&H55'  
```  
  
 Určuje, že název klíče `testhex` je **DWORD** hodnota nastavena na hexadecimální 55 (decimal 85). Poznámka: Tento formát dodržuje **& H** zápis jako nalezena ve specifikaci jazyka Visual Basic.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření skriptů registrátoru](../atl/creating-registrar-scripts.md)

