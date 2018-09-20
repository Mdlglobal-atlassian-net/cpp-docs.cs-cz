---
title: Průvodce přidáním členské proměnné | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.variable.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Member Variable Wizard [C++]
ms.assetid: 73e8fa99-ac1a-42e2-8fc2-4684b9eb6d4d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e53f9075648d5ea0d2c02e98be30c3c43a87f335
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396802"
---
# <a name="add-member-variable-wizard"></a>Průvodce přidáním členské proměnné

Tento průvodce přidá deklaraci členské proměnné do záhlaví souborů a v závislosti na možnostech, můžete přidat kód do souboru .cpp. Po přidání členské proměnné pomocí průvodce, můžete upravit kód ve vývojovém prostředí.

- **Přístup**

   Nastaví přístup k členské proměnné. Modifikátory přístupu jsou klíčová slova, které určují přístup jiných tříd k členské proměnné. Zobrazit [řízení přístupu členů](../cpp/member-access-control-cpp.md) pro další informace o zadávání přístupu. Úroveň přístup k proměnným členů je nastavena na **veřejné** ve výchozím nastavení.

- [public](../cpp/public-cpp.md)

- [protected](../cpp/protected-cpp.md)

- [private](../cpp/private-cpp.md)

- **Typ proměnné**

   Nastaví návratový typ pro členské proměnné, které chcete přidat.

   - Pokud přidáváte členské proměnné, která není ovládací prvek dialogového okna, vyberte ze seznamu dostupných typů.

      Informace o typech najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).

      |||
      |-|-|
      |**char**|**short**|
      |**double**|**unsigned char**|
      |**float**|**unsigned int**|
      |**int**|**unsigned long**|
      |**long**||

   - Pokud přidáváte členské proměnné pro ovládací prvek dialogového okna, je toto pole vyplněna typ objektu vrácený pro ovládací prvek nebo hodnotu. Pokud vyberete **ovládací prvek**, pak **typ proměnné** určuje základní třídu vyberete ovládací prvek **ID ovládacího prvku** pole. Pokud ovládací prvek dialogového okna pole může obsahovat hodnotu, a pokud vyberete **hodnotu**, pak **typ proměnné** určuje odpovídající typ hodnoty, který může obsahovat ovládací prvek. Zobrazit [ovládací prvky dialogového okna a typy proměnných](../ide/dialog-box-controls-and-variable-types.md) Další informace.

      Tato hodnota závisí na výběr v **ID ovládacího prvku** a nedá se změnit.

- **Název proměnné**

   Nastaví název členské proměnné, které chcete přidat. Členské proměnné obvykle začínají identifikační řetězec "m_", která je ve výchozím nastavení za vás.

- **Proměnné ovládacího prvku.**

   Označuje, že spravuje členskou proměnnou ovládacího prvku dialogové okno s [výměny dat a ověřování dat](../mfc/dialog-data-exchange-and-validation.md) podporovat. Zobrazit [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) Další informace. Tato možnost je dostupná jenom pro členské proměnné přidány do třídy odvozené od [CDialog](../mfc/reference/cdialog-class.md). Zaškrtněte toto políčko, chcete-li aktivovat **ID ovládacího prvku** a **ovládací prvek typu** možnosti.

- **ID ovládacího prvku**

   Nastaví ID pro ovládací prvek proměnnou, kterou chcete přidat. Vyberte ze seznamu ID pro typ ovládacího prvku, pro který chcete přidat členskou proměnnou. V seznamu je účinné pouze tehdy, když **řídicí proměnná** je zaškrtnuté políčko, a je omezená na ID pro ovládací prvky již přidán do dialogového okna. Například pro standardní **OK** je ID ovládacího prvku tlačítko, **IDOK**.

   |Možnost|Popis|
   |------------|-----------------|
   |**Ovládací prvek**|Tato možnost je nastavena ve výchozím nastavení pro typ ovládacího prvku. Spravuje samotného a nikoli na stav nebo obsah ovládacího prvku (jak je můžete chtít provést v seznamu, pole se seznamem nebo upravit) ovládacího prvku.|
   |**Hodnota**|Tato možnost je dostupná pouze pro typy ovládacích prvků, které mohou obsahovat hodnotu (například do textového pole) nebo odráží stav (jako je například zaškrtávací políčko) a pro které může spravovat rozsahu, obsah nebo stavu. Zobrazit [ovládací prvky dialogového okna a typy proměnných](../ide/dialog-box-controls-and-variable-types.md) Další informace.|

- **Kategorie**

   Určuje, zda je proměnná založená na typu ovládacího prvku nebo hodnota ovládacího prvku.

- **Typ ovládacího prvku**

   Nastaví typ ovládacího prvku přidán. Toto políčko není možné změnit. Například, že tlačítko má typ ovládacího prvku **tlačítko**, a má typ ovládacího prvku pole se seznamem **– pole se SEZNAMEM**. Zobrazit [ovládací prvky dialogového okna a typy proměnných](../ide/dialog-box-controls-and-variable-types.md) Další informace.

- **Maximální počet znaků**

   K dispozici pouze tehdy, když **typ proměnné** je nastavena na [CString](../atl-mfc-shared/reference/cstringt-class.md). Určuje maximální počet znaků, které může obsahovat ovládací prvek.

- **Minimální hodnota**

   K dispozici pouze v případě, že je typ proměnné **BOOL**, `int`, **UINT**, **dlouhé**, `DWORD`, **float**, **double**, **BAJTŮ**, **krátký**, [COLECurrency](../mfc/reference/colecurrency-class.md) nebo [CTime](../atl-mfc-shared/reference/ctime-class.md). Určuje přijatelné pro změnu nebo rozsah nejnižší hodnotu.

- **Maximální hodnota**

   K dispozici pouze v případě, že je typ proměnné **BOOL**, `int`, **UINT**, **dlouhé**, `DWORD`, **float**, **double**, **BAJTŮ**, **krátký**, `COLECurrency` nebo `CTime`. Určuje přijatelné pro změnu nebo rozsah nejvyšší hodnotu.

- **soubor .h**

   Pro ovládací prvky ActiveX, jejíž členské proměnné vyžadují obálkovou třídu. Nastaví název souboru hlavičky k přidání deklarace třídy.

- **soubor .cpp**

   Pro ovládací prvky ActiveX, jejíž členské proměnné vyžadují obálkovou třídu. Nastaví název implementačního souboru přidat definici třídy.

- **Komentář**

   Komentář v souboru hlaviček pro členské proměnné.

## <a name="see-also"></a>Viz také

[Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)