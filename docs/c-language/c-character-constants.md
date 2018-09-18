---
title: Konstanty znaků jazyka C | Dokumentace Microsoftu
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
ms.openlocfilehash: f9908bfd8be662a53727e9c833626f329dd45c04
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038578"
---
# <a name="c-character-constants"></a>Konstanty znaků jazyka C

"Znaková konstanta" je tvořena uzavřením jednoho znaku reprezentovatelné znakové sady do jednoduchých uvozovek (**""**). Znakové konstanty se používají k vyjádření znaků ve [znaková sada spuštění](../c-language/execution-character-set.md).

## <a name="syntax"></a>Syntaxe

*Znaková konstanta*: **"** *c-char pořadí* **.**

**L "** *c-char pořadí* **.**

*c – znak sekvence*: *c-char*

*c – znak sekvence jazyka c-char*

*c – znak*: žádný člen zdrojové znakové sady kromě jednoduché uvozovky (**"**), zpětného lomítka (**\\**), nebo znak nového řádku

*řídicí sekvence*

*řídicí sekvence*: *simple-escape-sequence*

*osmičková řídicí sekvence*

*šestnáctková řídicí sekvence*

*Simple-escape-sequence*: jeden z **\a \b \f \n \r \t \v**

**\\' \\" \\\ \\?**

*osmičková řídicí sekvence*: **\\** *uveden jako osmičková číslice* 

**\\**  *uveden jako osmičková číslice osmičkovými číslicemi*

**\\**  *uveden jako osmičková číslice uveden jako osmičková číslice osmičkovými číslicemi*

*šestnáctková řídicí sekvence*: **\x***šestnáctkové číslice* 

*šestnáctková řídicí sekvence šestnáctkové číslice*

## <a name="see-also"></a>Viz také

[Konstanty jazyka C](../c-language/c-constants.md)