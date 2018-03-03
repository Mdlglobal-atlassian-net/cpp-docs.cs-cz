---
title: "Volání s proměnlivým počtem argumentů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- arguments [C++], function
- arguments [C++], variable number of
- VARARGS.H
- ellipses (...), variable number of arguments
- STDARGS.H
- function calls, arguments
- '... ellipsis'
- function calls, variable number of arguments
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 446e15a6f578413cf3f0ddefa980303c10a5d280
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="calls-with-a-variable-number-of-arguments"></a>Volání s proměnlivým počtem argumentů
Seznam částečné parametrů můžete ukončí se třemi tečkami zápis, čárku, za nímž následuje tři tečky (**,...** ), k označení, že může být více argumentů předaný funkci, ale žádné další informace jsou uvedeny o nich. Na těchto argumentech se neprovádí kontrola typu. Zápis tří teček musí předcházet alespoň jeden parametr a tento zápis tří teček musí být posledním tokenem v seznamu parametrů. Bez zápisu tří teček není chování funkce definováno, pokud obdrží jiné parametry než ty deklarované v seznamu parametrů.  
  
 Chcete-li funkci zavolat s proměnným počtem argumentů, stačí ve volání funkce zadat libovolný počet argumentů. Příkladem je funkce `printf` z knihovny modulu runtime jazyka C. Volání funkce musí obsahovat jeden argument pro každý název typu, který je deklarován v seznamu parametrů nebo v seznamu typů argumentů.  
  
 Všechny argumenty zadané ve volání funkce jsou umístěny na zásobník, pokud není zadána konvence volání `__fastcall`. Počet parametrů deklarovaných pro funkci určuje, kolik argumentů je odebráno ze zásobníku a přiřazeno parametrům. Jste zodpovědní za načtení jakýchkoli dalších argumentů ze zásobníku a za určení počtu přítomných argumentů. Soubor STDARG.H obsahuje makra ve stylu standardu ANSI pro přístup k argumentům funkce, která přijímá proměnný počet argumentů. Také jsou stále podporována makra ve stylu XENIX v souboru VARARGS.H.  
  
 Tato ukázka deklarace je funkcí, kterou lze volat s proměnným počtem argumentů:  
  
```  
int average( int first, ...);  
```  
  
## <a name="see-also"></a>Viz také  
 [Volání funkcí](../c-language/function-calls.md)