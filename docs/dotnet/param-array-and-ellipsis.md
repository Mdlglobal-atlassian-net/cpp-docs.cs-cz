---
title: Pole parametrů a třemi tečkami | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function overloading, argument matching
ms.assetid: 492e3f6c-1c4c-4e0c-a358-72f2d39c30be
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: f6d256fd48d8c9f206619e6baa9a50a0278d30c3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="param-array-and-ellipsis"></a>Pole parametrů a tlačítko se třemi tečkami
Prioritu pole parametrů pro rozlišování volání přetížené funkce změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 Ve spravovaných rozšíření a nové syntaxe neexistuje žádné explicitní podporu pro pole parametrů, který podporuje C# a Visual Basic. Místo toho jeden flags obyčejnou pole s atributem, následujícím způsobem:  
  
```  
void Trace1( String* format, [ParamArray]Object* args[] );  
void Trace2( String* format, Object* args[] );  
```  
  
 Při těchto obě vypadají stejně, `ParamArray` atribut to značky pro C# nebo jiných jazyků CLR jako pole trvá proměnné počet elementů s každým vyvolání. Změna v chování v programech mezi spravovaných rozšíření a nové syntaxe je rozlišení přetížené funkce nastavit ve které jedna instance deklaruje tři tečky a druhý deklaruje `ParamArray` atributů, jako v následujícím příkladu poskytované Artur Laksberg.  
  
```  
int fx(...); // 1  
int fx( [ParamArray] Int32[] ); // 2  
```  
  
 Ve spravovaných rozšíření se třemi tečkami byl přednost atribut, který je možné logicky, protože atribut není formální aspekt jazyka. V nové syntaxe, ale pole parametrů se teď podporuje přímo v jazyce a ho má přednost se třemi tečkami vzhledem k tomu, že je více silného typu. Proto v spravovaných rozšíření volání  
  
```  
fx( 1, 2 );  
```  
  
 přeloží na `fx(...)` v nové syntaxe přeloží na `ParamArray` instance. Na vypnutém pravděpodobnost, že vaše chování program závisí na volání instance třemi tečkami přes u `ParamArray`, budete muset upravit podpis nebo volání.  
  
## <a name="see-also"></a>Viz také  
 [Obecné jazykové změny (C++/CLI)](../dotnet/general-language-changes-cpp-cli.md)