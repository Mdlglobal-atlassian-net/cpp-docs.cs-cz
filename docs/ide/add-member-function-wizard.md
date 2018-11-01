---
title: Průvodce přidáním členské funkce
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.function.overview
helpviewer_keywords:
- Add Member Function Wizard [C++]
ms.assetid: 13b6defc-faa6-4d57-83db-9dd854cbea3d
ms.openlocfilehash: 6ba95026d712c71a9d706baddfefda548100c64a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615043"
---
# <a name="add-member-function-wizard"></a>Průvodce přidáním členské funkce

Tento průvodce přidá do souboru hlaviček a implementace členské funkce zástupných procedur do souboru implementace pro vybranou třídu deklaraci členské funkce.

Po přidání členské funkce pomocí průvodce, můžete upravit kód ve vývojovém prostředí.

- **Návratový typ**

   Nastaví návratový typ pro členské funkce, které chcete přidat. Můžete zadat vlastní návratový typ, nebo můžete vybrat ze seznamu dostupných typů. Informace o typech najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).

   ||||
   |-|-|-|
   |**char**|**int**|**unsigned int**|
   |**double**|**long**|**unsigned long**|
   |**float**|**short**|**void**|
   |`HRESULT`|**unsigned char**||

- **Název funkce**

   Nastaví název členské funkce, které chcete přidat.

- **Typ parametru**

   Nastaví typ parametru, který chcete přidat pro členskou funkci, pokud členskou funkci obsahuje parametry. Můžete zadat vlastní typ parametru, nebo můžete vybrat ze seznamu dostupných typů.

   ||||
   |-|-|-|
   |**char**|**int**|**unsigned char**|
   |**double**|**long**|**unsigned int**|
   |**float**|**short**|**unsigned long**|

- **Název parametru**

   Nastaví název parametru, který chcete přidat pro členskou funkci, pokud členskou funkci obsahuje parametry.

- **Seznam parametrů**

   Zobrazí seznam parametrů, které jste přidali na členskou funkci. Přidání parametru do seznamu, zadejte typ a název v **typ parametru** a **název parametru** políčka a klikněte na tlačítko **přidat**. Odebrat parametr ze seznamu, vyberte parametr a klikněte na **odebrat**.

- **Přístup**

   Nastaví přístup na členskou funkci. Modifikátory přístupu jsou klíčová slova, které určují přístup jiných tříd na členskou funkci. Zobrazit [řízení přístupu členů](../cpp/member-access-control-cpp.md) pro další informace o zadávání přístupu. Úroveň přístupu členské funkce je nastavena na **veřejné** ve výchozím nastavení.

   - [public](../cpp/public-cpp.md)

   - [protected](../cpp/protected-cpp.md)

   - [private](../cpp/private-cpp.md)

   Zkontrolujte, jestli nové členské funkce jsou statická nebo virtuální, a zda je vložené nebo čistě. Pokud nastavíte členské funkce bude čistý, `Virtual` zaškrtávací políčko zaškrtnuto a **vložené** zaškrtávací políčko je k dispozici. Výchozí hodnota je nevirtuální, nestatické členské funkce.

   |Možnost|Popis|
   |------------|-----------------|
   |[Static](../cpp/storage-classes-cpp.md)|Určuje, že funguje jako globální funkci a může být volána mimo třídu, i s bez vytvoření instance třídy. Členská funkce nemá přístup k nestatické členy. Členská funkce definována jako `Static` nemůže být virtuální.|
   |[Virtuální](../cpp/virtual-cpp.md)|Zajišťuje, že správné členská funkce je volána pro objekt, bez ohledu na výraz použitý k volání členské funkce. Členská funkce definována jako `Virtual` nemohou být statické.|
   |**pure**|Označuje, že pro virtuální členské funkce deklarované; není dodávána žádná implementace Proto **prázdná** se dá nastavit jenom pro virtuální členské funkce. Třídu, která obsahuje alespoň jeden čistě virtuální členská funkce je považována za abstraktní třídu. Třídy odvozené od abstraktní třídy musí implementovat čistě virtuální členské funkci nebo, příliš, jsou abstraktní třídy.|
   |[vložené](../cpp/inline-functions-cpp.md)|Dává pokyn kompilátoru k vložení kopie těla členské funkce do každé místo, kde má členská funkce je volána. Členská funkce definována jako **vložené** nemůže být prázdná.|

- **soubor .cpp**

   Nastaví umístění souboru, do níž je zapsána implementace se zakázaným inzerováním členské funkce. Ve výchozím nastavení se zapisují do souboru CPP pro třídy, do kterého se přidá členskou funkci. Klikněte na tlačítko se třemi tečkami změňte název souboru. Obsah vybraný soubor se přidá implementace členské funkce.

- **Komentář**

   Komentář v souboru hlaviček pro členské funkce.

- **Signatura funkce**

   Zobrazí členská funkce, které je uvedeno v kódu po kliknutí na **Dokončit**. Text v tomto poli nelze upravit. Chcete-li změnit členská funkce, změňte do příslušných polí v průvodci.

## <a name="see-also"></a>Viz také

[Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)