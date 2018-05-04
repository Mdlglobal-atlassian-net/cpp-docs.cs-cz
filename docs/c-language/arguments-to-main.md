---
title: Argumenty operace main | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 544b5eaba49fff0a5f2b3111c2a5f7fe42c9b2ee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="arguments-to-main"></a>Argumenty operace main
**ANSI 2.1.2.2.1** sémantika argumenty operace Main  
  
 V Microsoft C je volána funkce volána při spuštění programu **hlavní**. Neexistuje žádné prototypu deklarovat pro **hlavní**, a může být definován s nula, dvě nebo tři parametry:  
  
```  
int main( void )  
int main( int argc, char *argv[] )  
int main( int argc, char *argv[], char *envp[] )  
```  
  
 Ve třetím řádku výše, kde **hlavní** přijímá tři parametry, je rozšíření Microsoft standardu ANSI C. Třetí parametr **envp –**, je pole ukazatele na proměnné prostředí. **Envp –** pole se ukončila příkazem ukazatele null. V tématu [hlavní funkce a spuštění programu](../c-language/main-function-and-program-execution.md) Další informace o **hlavní** a **envp –**.  
  
 Proměnná **argc –** nikdy obsahuje zápornou hodnotu.  
  
 Pole řetězců končí **argv – [argc –]**, který obsahuje ukazatele null.  
  
 Všechny elementy **argv –** pole jsou ukazatele na řetězce.  
  
 Program volána bez argumentů příkazového řádku se zobrazí na hodnotu jedna pro **argc –**, protože název spustitelného souboru je umístěn v **argv – [0]**. (V operačním systému MS-DOS verze dřívější než 3.0 není název spustitelného souboru k dispozici. Písmenem "C" je umístěn v **argv – [0]**.) Řetězce na kterou odkazuje **argv – [1]** prostřednictvím **argv – [argc – - 1]** představují parametry programu.  
  
 Parametry **argc –** a **argv –** lze měnit a zachovat jejich poslední uložené hodnoty mezi spuštění programu a ukončení programu.  
  
## <a name="see-also"></a>Viz také  
 [Prostředí](../c-language/environment.md)