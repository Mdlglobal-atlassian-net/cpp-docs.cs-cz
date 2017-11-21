---
title: "C2558 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2558
dev_langs: C++
helpviewer_keywords: C2558
ms.assetid: 822b701e-dcae-423a-b21f-47f36aff9c90
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b11827ed70609a83be9e63de2af3d3b8f12d2310
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2558"></a>C2558 chyby kompilátoru
Identifikátor: není k dispozici konstruktor kopie nebo je konstruktor kopie deklarován explicitně  
  
 Konstruktor kopie inicializuje objekt z jiného objektu stejného typu. (Vytvoří kopii tohoto objektu.) Pokud nedefinujete žádné konstruktory, vygeneruje kompilátor výchozí kopii.  
  
### <a name="to-fix-this-error"></a>Odstranění této chyby  
  
1.  Problému může dojít, když je proveden pokus o zkopírování třídu, jejíž kopírovací konstruktor je `private`. Ve většině případů třídy, který má `private` kopírovat kopírovacího konstruktoru. Běžné programovací technika deklaruje `private` kopírovacího konstruktoru zabránit přímé používání třídy. Tato třída může být sama o sobě nepoužitelná nebo ke správné funkci vyžaduje jinou třídu.  
  
     Pokud zjistíte, že je bezpečné použití třídy, která má `private` kopírovací konstruktor, novou třídu odvozena od třídy, která má `private` konstruktor a zkontrolujte `public` nebo `protected` kopírovacího konstruktoru, které jsou k dispozici v nové třídy. Použijte odvozenou třídu namísto původní.  
  
2.  Problému může dojít, když je proveden pokus o zkopírování třídu, jejíž kopírovací konstruktor je explicitní. Deklarování kopírovacího konstruktoru jako `explicit` brání předávání nebo vrácení objekty třídy do nebo z funkcí. Další informace o explicitní konstruktory najdete v tématu [uživatelem definované převody typů](../../cpp/user-defined-type-conversions-cpp.md).  
  
3.  Problému může dojít, když je proveden pokus o kopírování instance třídy deklarován `const` pomocí kopírovacího konstruktoru, které nevyžaduje `const` odkazovat na parametr. Vaše kopie konstruktor s deklarovat `const` odkaz místo bez const typu odkaz na typ.