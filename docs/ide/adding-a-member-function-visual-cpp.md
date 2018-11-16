---
title: Přidat členskou funkci
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.member.function
- vc.codewiz.function.overview
helpviewer_keywords:
- member functions, adding to classes
- classes [C++], adding members
- add member function wizard [C++]
ms.assetid: 55b25ddb-541d-44ed-957c-974ef91cfc85
ms.openlocfilehash: 1cd7abbbc43ae56861b3b83451b41933b8b0b4f0
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693409"
---
# <a name="add-a-member-function"></a>Přidat členskou funkci

V **zobrazení tříd**, můžete přidat členskou funkci na všechny třídy. Když toto provedete, deklarací se přidá do souboru hlaviček a těla členské funkce se zakázaným inzerováním se přidá do souboru implementace třídy, který poté můžete upravit.

**Chcete-li přidat členskou funkci na třídu:**

1. V **zobrazení tříd**, rozbalte uzel projektu pro zobrazení tříd v projektu. (Chcete-li otevřít **zobrazení tříd**, na panelu nabídek zvolte **zobrazení**, **zobrazení tříd**.)

1. Otevřete místní nabídku pro třídu, kterou chcete přidat členskou funkci, a klikněte na tlačítko **přidat**, **přidat funkci**.

1. Poskytnout patřičné podrobné informace o členskou funkci. Další informace najdete v tématu [Průvodce přidáním členské funkce](#add-member-function-wizard).

1. Zvolte **Dokončit** pro vygenerování kódu členské funkce.

## <a name="in-this-section"></a>V tomto oddílu

- [Průvodce přidáním členské funkce](#add-member-function-wizard)

## <a name="add-member-function-wizard"></a>Průvodce přidáním členské funkce

Tento průvodce přidá do souboru hlaviček deklaraci členské funkce. Prázdná implementace členské funkce také přidá do souboru implementace pro vybranou třídu.

Po přidání členské funkce pomocí průvodce, můžete upravit kód ve vývojovém prostředí.

- **Návratový typ**

  Nastaví návratový typ pro členskou funkci, kterou chcete přidat. Můžete zadat vlastní návratový typ, nebo můžete vybrat ze seznamu dostupných typů. Informace o typech najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned int` |
  | `double` | `long` | `unsigned long` |
  | `float` | `short` | `void` |
  | `HRESULT` | `unsigned char` | |

- **Název funkce**

  Nastaví název členské funkce, kterou chcete přidat.

- **Typ parametru**

  Nastaví typ parametru, který přidáváte členské funkce, pokud členskou funkci obsahuje parametry. Můžete zadat vlastní typ parametru, nebo můžete vybrat ze seznamu dostupných typů.

  | | | |
  |---|---|---|
  | `char` | `int` | `unsigned char` |
  | `double` | `long` | `unsigned int` |
  | `float` | `short` | `unsigned long` |

- **Název parametru**

  Nastaví název parametru, který přidáváte členské funkce, pokud členskou funkci obsahuje parametry.

- **Seznam parametrů**

  Zobrazí seznam parametrů, které jste přidali na členskou funkci. Přidání parametru do seznamu, zadejte typ a název v **typ parametru** a **název parametru** pole a vyberte **přidat**. Chcete-li odebrat parametr ze seznamu, vyberte parametr a vyberte **odebrat**.

- **Přístup**

  Nastaví přístup na členskou funkci. Modifikátory přístupu jsou klíčová slova, které určují přístup jiných tříd na členskou funkci. Další informace o zadávání přístup, najdete v části [řízení přístupu členů](../cpp/member-access-control-cpp.md). Úroveň přístupu členské funkce je nastavena na `public` ve výchozím nastavení.

  - [public](../cpp/public-cpp.md)
  - [protected](../cpp/protected-cpp.md)
  - [private](../cpp/private-cpp.md)

  Zkontrolujte, jestli nové členské funkce jsou statická nebo virtuální, a zda je vložené nebo čistě. Pokud nastavíte členské funkce bude čistý, **virtuální** zaškrtávací políčko zaškrtnuto a **vložené** zaškrtávací políčko je k dispozici. Výchozí hodnota je nevirtuální, nestatické členské funkce.

  | Možnost | Popis |
  |--------|-------------|
  | [Static](../cpp/storage-classes-cpp.md) |  Určuje, že funguje jako globální funkci a může být volána mimo třídu i bez vytvoření instance třídy. Členská funkce nemá přístup k nestatické členy. Členská funkce definována jako `Static` nemůže být virtuální. |
  | [Virtuální](../cpp/virtual-cpp.md) | Zajišťuje, že správné členská funkce je volána pro objekt, bez ohledu na výraz použitý k volání členské funkce. Členská funkce definována jako `Virtual` nemohou být statické. |
  | **pure** | Označuje, že pro virtuální členské funkce deklarované není dodávána žádná implementace. **Čistě** se dá nastavit jenom pro virtuální členské funkce. Třídu, která obsahuje alespoň jeden čistě virtuální členská funkce je považována za abstraktní třídu. Třídy odvozené od abstraktní třídy musí implementovat čistě virtuální členské funkci nebo, příliš, jsou abstraktní třídy. |
  | [vložené](../cpp/inline-functions-cpp.md) | Dává pokyn kompilátoru k vložení kopie těla členské funkce do každé místo, kde má členská funkce je volána. Členská funkce definována jako **vložené** nemůže být prázdná. |

- **soubor .cpp**

  Nastaví umístění souboru, do níž je zapsána implementace se zakázaným inzerováním členské funkce. Ve výchozím nastavení se zapisují do souboru CPP pro třídy, do kterého se přidá členskou funkci. Vyberte tlačítko se třemi tečkami změňte název souboru. Obsah vybraný soubor se přidá implementace členské funkce.

- **Komentář**

  Komentář v souboru hlaviček pro členské funkce.

- **Signatura funkce**

  Členská funkce převzat z kódu se zobrazí při výběru **Dokončit**. Text v tomto poli nelze upravit. Chcete-li změnit členská funkce, změňte do příslušných polí v průvodci.
