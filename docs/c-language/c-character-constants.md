---
title: Konstanty znaků jazyka C | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- characters, constants
- (') single quotation mark
- constants, character
- single quotation mark
ms.assetid: 388ae7d7-2c3a-44d6-a507-63f541ecd2da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0009f795936da7eb0c2ff69aa192e8f609638d2f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32382283"
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