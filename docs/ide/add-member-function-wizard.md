---
title: "Průvodce přidáním členské funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.function.overview
dev_langs: C++
helpviewer_keywords: Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 775b519b304549b474cd21980ef5a4cbe8f2d4d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="add-member-function-wizard"></a>Průvodce přidáním členské funkce
Tento průvodce přidá deklaraci členské funkce soubor hlaviček a implementaci do souboru implementace pro vybrané třídy.  
  
 Po přidání členské funkce pomocí průvodce, můžete upravit kód ve vývojovém prostředí.  
  
 **Návratový typ**  
 Nastaví návratový typ pro funkci člen, který chcete přidat. Můžete zadat vlastní návratový typ, nebo můžete vybrat ze seznamu dostupných typů. Informace o typech najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned int`|  
|**double**|**long**|`unsigned long`|  
|**float**|**short**|`void`|  
|`HRESULT`|`unsigned char`||  
  
 **Název funkce**  
 Nastaví název členské funkce, kterou chcete přidat.  
  
 **Typ parametru**  
 Nastaví typ parametru, který přidáváte členské funkce, pokud funkci člen má parametry. Můžete zadat vlastní typ parametru, nebo můžete vybrat ze seznamu dostupných typů.  
  
||||  
|-|-|-|  
|`char`|`int`|`unsigned char`|  
|**double**|**long**|`unsigned int`|  
|**float**|**short**|`unsigned long`|  
  
 **Název parametru**  
 Nastaví název parametru, který přidáváte členské funkce, pokud funkci člen má parametry.  
  
 **Seznam parametrů**  
 Zobrazí seznam parametrů, které jste přidali do členské funkce. Pro přidání parametru do seznamu, zadejte typ a název **typ parametru** a **název parametru** políčka a klikněte na tlačítko **přidat**. Chcete-li parametr odebrat ze seznamu, vyberte parametr a klikněte na **odebrat**.  
  
 **Přístup**  
 Nastaví přístupu k funkci člen. Modifikátory přístupu jsou klíčová slova, která určující přístup ostatní třídy mají členské funkce. V tématu [řízení přístup ke členu](../cpp/member-access-control-cpp.md) pro další informace o přístupu. Úroveň přístupu funkce členů je nastavena na **veřejné** ve výchozím nastavení.  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 Zkontrolujte, jestli jsou nové funkce člen statická nebo virtuální, a zda je vložené nebo prázdná. Pokud nastavíte členskou funkci jako prázdnou, `Virtual` je zaškrtnuté políčko a **vložené** zaškrtávací políčko je k dispozici. Výchozí hodnota je nevirtuální, nestatické členské funkce.  
  
|Možnost|Popis|  
|------------|-----------------|  
|[Static](../cpp/storage-classes-cpp.md)|Určuje, že funkce chová jako globální a lze volat mimo třídu, i když bez vytváření instance třídy. Členská funkce nemá přístup k nestatické členy. Členské funkce zadaná jako `Static` nemůže být virtuální.|  
|[Virtuální](../cpp/virtual-cpp.md)|Zajišťuje, že pro objekt, bez ohledu na to výraz použitý k volání členské funkce je volána funkce správné člen. Členské funkce zadaná jako `Virtual` nemůže být statická.|  
|**Čistý**|Označuje, žádné implementace jsou dodané pro člena virtuální funkci se deklarovat; Proto **prázdná** lze zadat pouze u člena virtuální funkce. Třída, která obsahuje alespoň jeden prázdné virtuální členské funkce považuje za abstraktní třídu. Třídy odvozené od abstraktní třídy musí implementovat prázdné virtuální členské funkce nebo, příliš, jsou abstraktní třídy.|  
|[Vložené](../cpp/inline-functions-cpp.md)|Dá pokyn kompilátoru vložení kopii tělo funkce člena do každé místo, kde je volána funkce člen. Členské funkce zadaná jako **vložené** nemůže být prázdná.|  
  
 **souboru**  
 Nastaví umístění souboru, do níž je zapsána implementaci. Ve výchozím nastavení se zapisují do souboru pro třídu, ke kterému se přidá – členská funkce. Klikněte na tlačítko se třemi tečkami změňte název souboru. Implementace členské funkce se přidá do obsah vybraného souboru.  
  
 **Komentář**  
 Komentář v záhlaví souboru – členská funkce.  
  
 **Podpis funkce**  
 Zobrazí – členská funkce, které je uvedeno v kódu po kliknutí na tlačítko **Dokončit**. Text v tomto poli nelze upravit. Chcete-li změnit členskou funkci, změňte do příslušných polí v průvodci.  
  
## <a name="see-also"></a>Viz také  
 [Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)