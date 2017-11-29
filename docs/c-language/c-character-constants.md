---
title: "Konstanty znaků jazyka C | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 70525e774ea7c89cbd767b607a142d338b797df3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="c-character-constants"></a>Konstanty znaků jazyka C
"Konstanta znaků" je vytvořen uzavřením jeden znak z reprezentovat znakovou sadu do jednoduchých uvozovek (**' '**). Konstanty znaků se používají k vyjádření znaků [znaková sada spuštění](../c-language/execution-character-set.md).  
  
## <a name="syntax"></a>Syntaxe  
 *Konstanta znaků*:  
 **'** *c-char pořadí* **.**  
  
 **L "** *c-char pořadí* **.**  
  
 *c – znak pořadí*:  
 *c – znak*  
  
 *c – znak pořadí c-char*  
  
 *c – znak*:  
 Nastavit kteréhokoli člena znak zdroje, s výjimkou jednoduché uvozovky (**'**), zpětné lomítko (**\\**), nebo znak nového řádku  
  
 *řídicí sekvence*  
  
 *řídicí sekvence*:  
 *jednoduché – řídicí sekvence*  
  
 *osmičková řídicí sekvence*  
  
 *hexadecimální – řídicí sekvence*  
  
 *jednoduché – řídicí sekvence*: jeden z  
 **\a \b \f \n \r \t \V**  
  
 **\\' \\" \\\ \\?**  
  
 *osmičková řídicí sekvence*:  
 **\\**  *osmičková číslice*  
  
 **\\**  *osmičková číslice osmičková číslice*  
  
 **\\**  *osmičková číslice osmičková osmičková číslice číslic*  
  
 *hexadecimální – řídicí sekvence*:  
 **\x***šestnáctková číslice*   
  
 *hexadecimální číslice hexadecimální – řídicí sekvence*  
  
## <a name="see-also"></a>Viz také  
 [Konstanty jazyka C](../c-language/c-constants.md)