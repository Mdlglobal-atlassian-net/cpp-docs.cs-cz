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
ms.workload: cplusplus
ms.openlocfilehash: cff2cb402da87cf37d2f63350088ce4256f3b44c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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