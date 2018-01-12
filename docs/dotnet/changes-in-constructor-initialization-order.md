---
title: "Změny v pořadí inicializace konstruktoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: constructors, C++
ms.assetid: 8892c38d-6bf7-4cf7-ac8f-15e052135a79
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 499855ec5052c039e007df8348db094aee356411
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changes-in-constructor-initialization-order"></a>Změny v pořadí inicializace konstruktoru
Pořadí inicializace konstruktorů třídy změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
## <a name="comparison-of-constructor-initialization-order"></a>Porovnání pořadí inicializace konstruktoru  
 V části spravovaných rozšíření pro C++ inicializace konstruktoru došlo k chybě v následujícím pořadí:  
  
1.  Konstruktor základní třídy, pokud existuje, je vyvolána.  
  
2.  Inicializace seznamu třídy je vyhodnocena.  
  
3.  Provede se tělo kód konstruktoru třídy.  
  
 Toto pořadí provádění dodržovat stejné konvence jako nativní C++ programování. Nový jazyk Visual C++ předepisuje následující pořadí zpracování pro třídy CLR:  
  
1.  Inicializace seznamu třídy je vyhodnocena.  
  
2.  Konstruktor základní třídy, pokud existuje, je vyvolána.  
  
3.  Provede se tělo kód konstruktoru třídy.  
  
 Všimněte si, že tato změna se vztahuje pouze na třídy modulu CLR; nativní třídy v jazyce Visual C++ stále předchozí konvence. V obou případech pořadí těchto pravidel výše v celém řetězci celou hierarchii dané třídy.  
  
 Vezměte v úvahu následující příklad kódu pomocí spravovaných rozšíření pro C++:  
  
```  
__gc class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
__gc class B : public A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 Následující pořadí inicializace konstruktoru předepsané výše, bychom měli vidět následující pořadí provádění při vydání nových instancí třídy `B` se vytvářejí:  
  
1.  Konstruktor základní třídy `A` je volána. `_n` Je inicializován na `1`.  
  
2.  Inicializace seznamu pro třídu `B` vyhodnotí. `_m` Je inicializován na `1`.  
  
3.  Kód tělo třídy `B` se spustí.  
  
 Nyní zvažte stejný kód v nové syntaxe jazyka Visual C++:  
  
```  
ref class A  
{  
public:  
   A() : _n(1)  
   {  
   }  
  
protected:  
   int _n;  
};  
  
ref class B : A  
{  
public:  
   B() : _m(_n)  
   {  
   }  
private:  
   int _m;  
};  
```  
  
 Pořadí zpracování při vydání nových instancí třídy `B` se vytvářejí v rámci nové syntaxe je:  
  
1.  Inicializace seznamu pro třídu `B` vyhodnotí. `_m` Je inicializován na `0` (`0` je Neinicializovaný hodnota `_m` člen třídy).  
  
2.  Konstruktor základní třídy `A` je volána. `_n` Je inicializován na `1`.  
  
3.  Kód tělo třídy `B` se spustí.  
  
 Všimněte si, že podobná syntaxe způsobí odlišné výsledky pro tyto příklady kódu. Konstruktoru třídy `B` závisí na hodnotu ze základní třídy `A` k inicializaci jejího člena. Ale v konstruktoru pro třídu `A` ještě nebyla vyvolána. Tato závislost může být nebezpečné hlavně, když zděděná třída závisí na paměti nebo prostředků přidělování v konstruktoru základní třídy.  
  
## <a name="what-this-means-going-from-managed-extensions-for-c-to-visual-c-2010"></a>Co znamená tento přechod ze spravovaných rozšíření jazyka C++ na Visual C++ 2010  
 V mnoha případech by mělo být změny pořadí spuštění konstruktory tříd pro programátorů transparentní, protože základní třídy mají žádné představu o chování zděděné třídy. Ale jak tyto příklady kódu ukazují, konstruktory zděděné třídy mohou být výrazně ovlivněny při jejich inicializační seznamy závisí na hodnotách členy základní třídy. Když přesouváte kódu ze spravovaných rozšíření jazyka C++ na novou syntaxi, zvažte přesunutí těchto konstrukcí k tělu konstruktoru třídy, kde provádění záruku, že objevit jako poslední.  
  
## <a name="see-also"></a>Viz také  
 [Spravované typy (C + +/ CL)](../dotnet/managed-types-cpp-cl.md)   
 [Konstruktory](../cpp/constructors-cpp.md)   
 