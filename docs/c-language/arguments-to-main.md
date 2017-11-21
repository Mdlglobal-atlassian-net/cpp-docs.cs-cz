---
title: Argumenty operace main | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 39824fef-05ad-461d-ae82-49447dda8060
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: aa4dda9a8735f0b57dd6dcefa0f16774c006da35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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