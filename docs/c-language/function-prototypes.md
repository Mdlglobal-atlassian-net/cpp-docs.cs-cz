---
title: Funkce prototypy | Microsoft Docs
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
- function prototypes
- function return types, function prototypes
- data types [C], function return types
- functions [C], return types
- prototypes [C++], function
ms.assetid: d152f8e6-971e-432c-93ca-5a91400653c2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea02b5b3bb1517623a0c3fc67a752d203f81c5a8
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2018
---
# <a name="function-prototypes"></a>Prototypy funkcí
Deklarace funkce předchází v definici funkce a určuje název, návratový typ, třídy úložiště a dalších atributů funkce. Jako prototyp, třeba deklarace funkce vytvořit také typy a identifikátory pro argumenty funkce.  
  
## <a name="syntax"></a>Syntaxe  
 `declaration`:  
 *specifikátory deklarace atribut seq* opt*init. deklarátor seznamu* opt**;**  
  
 /\* *atribut seq* opt je specifické pro Microsoft * /  
  
 *specifikátory deklarace*:  
 *specifikátor třídy úložiště specifikátory deklarace* opt  
  
 *Specifikátor typu deklarace – specifikátory* opt  
  
 *Kvalifikátor typu deklarace – specifikátory* opt  
  
 *init-declarator-list*:  
 *init-declarator*  
  
 *init-declarator-list*  **,**  *init-declarator*  
  
 *init-declarator*:  
 *deklarátor*  
  
 *deklarátor = inicializátoru*  
  
 `declarator`:  
 *ukazatel* opt*přímo deklarátor*  
  
 *deklarátor přímo*: /\* deklarátor – funkce \*/  
 *deklarátor přímo***(***seznam parametrů typu***)** / * deklarátor nový styl       \*/  
  
 *deklarátor přímo***(***seznam identifikátorů* opt**)** / * deklarátor zastaralé stylu     \*/  
  
 Prototyp má stejné formuláře jako definice této funkce, s výjimkou toho, aby je ukončen středníkem hned za uzavírací kulatá závorka a proto nemá žádné body. V obou případech návratový typ, musíte souhlasit s návratovým typem zadaný v definici funkce.  
  
 Prototypy funkcí mají následující důležité používá:  
  
-   Vytvoří návratový typ pro funkce, které návratové typy jiné než `int`. I když funkce, které vracejí `int` hodnoty nevyžadují prototypy, prototypy doporučují.  
  
-   Bez dokončení prototypy standardní převody jsou vytvářeny, ale žádné pokusu o zkontrolujte typ a počet argumentů s počtem parametrů.  
  
-   Prototypy slouží k inicializaci ukazatelé na funkce, než jsou definovány tyto funkce.  
  
-   Seznam parametrů se používá pro kontrolu korespondence argumentů ve volání funkce s parametry v definici funkce.  
  
 Převedený typ každý parametr určuje výklad argumenty, které umístí volání funkce v zásobníku. Neshoda typu mezi parametrem a parametr může způsobit argumenty v zásobníku na dojít k nesprávné interpretaci. Například v počítači, 16bitové, pokud je ukazatel 16bitové předat jako argument, pak deklarován jako **dlouho** parametr první 32 bity v zásobníku se interpretují jako **dlouho** parametr. Tato chyba vytvoří problémy nejenom s **dlouho** parametr, ale žádné parametry, které následují ho. Chyby tohoto druhu, můžete zjistit pomocí deklarace prototypy dokončení funkcí pro všechny funkce.  
  
 Prototyp vytváří atributy funkce tak, aby volání funkce, která předchází jeho definice (nebo ke kterým došlo v jiné zdrojové soubory) může sloužit k typ argumentu a návratový typ neshody. Pokud zadáte třeba **statické** – specifikátor třídy úložiště v prototyp, musíte zadat také **statické** třídy úložiště v definici funkce.  
  
 Dokončení deklarace parametrů (`int a`) můžete kombinovat s deklarátory abstraktu jazyka (`int`) ve stejné deklaraci. Toto prohlášení je například právní informace:  
  
```  
int add( int a, int );  
```  
  
 Prototyp může obsahovat typ i identifikátor pro každý výraz, který je předat jako argument. Tyto identifikátory však mít rozsah pouze až do konce deklaraci. Prototyp můžete také odrážela skutečnost, že počet argumentů je proměnná nebo že jsou předán žádný argument. Bez tohoto seznamu nemusí být zjištěny neshody, kompilátor nemůže generovat diagnostické zprávy, které se jich týkají. V tématu [argumenty](../c-language/arguments.md) Další informace o kontrola typu.  
  
 Rozsah prototypu v kompilátoru Microsoft C je kompatibilní se specifikací ANSI nyní, když kompilujete s /Za – možnost kompilátoru. To znamená, že pokud je deklarovat `struct` nebo **sjednocení** značky v rámci prototyp značky je zadaný v tomto oboru, spíše než v globálním oboru. Například když kompilujete s /Za pro kompatibilita se specifikací ANSI, můžete nikdy volat tuto funkci bez získávání chybu neshody typu:  
  
```  
void func1( struct S * );  
```  
  
 Chcete-li váš kód, definovat nebo deklarovat `struct` nebo **sjednocení** v globálním oboru před prototyp funkce:  
  
```  
struct S;  
void func1( struct S * );  
```  
  
 V části /Ze je stále značky zadané v globálním oboru.  
  
## <a name="see-also"></a>Viz také  
 [Funkce](../c-language/functions-c.md)