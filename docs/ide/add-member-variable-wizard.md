---
title: Průvodce přidáním členské proměnné | Microsoft Docs
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
ms.openlocfilehash: f3ae6a3aef4bdf774b5630a9bb0b2a0b49f7f29b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="add-member-variable-wizard"></a>Průvodce přidáním členské proměnné
Tento průvodce přidá deklaraci členské proměnné soubor hlaviček a v závislosti na možnosti, můžete přidat kód do souboru. Po přidání členské proměnné pomocí průvodce, můžete upravit kód ve vývojovém prostředí.  
  
 **Přístup**  
 Nastaví přístupu k členské proměnné. Modifikátory přístupu jsou klíčová slova, která určující přístup ostatní třídy mají k členské proměnné. V tématu [řízení přístup ke členu](../cpp/member-access-control-cpp.md) pro další informace o přístupu. Úroveň proměnné přístupu členů je nastavena na **veřejné** ve výchozím nastavení.  
  
-   [public](../cpp/public-cpp.md)  
  
-   [protected](../cpp/protected-cpp.md)  
  
-   [private](../cpp/private-cpp.md)  
  
 **Typ proměnné**  
 Nastaví návratový typ pro proměnnou člen, který chcete přidat.  
  
-   Pokud přidáváte členské proměnné, která není ovládací prvek dialogového okna, vyberte ze seznamu dostupných typů.  
  
     Informace o typech najdete v tématu [základní typy](../cpp/fundamental-types-cpp.md).  
  
    |||  
    |-|-|  
    |`char`|**short**|  
    |**double**|`unsigned char`|  
    |**float**|`unsigned int`|  
    |`int`|`unsigned long`|  
    |**long**||  
  
-   Pokud přidáváte členské proměnné pro ovládací prvek dialogového okna, je toto políčko vyplněn typ objektu pro ovládací prvek nebo hodnota vrácena. Pokud vyberete **řízení**, pak **typ proměnné** určuje základní třídy, vyberte v ovládacího prvku **ID ovládacího prvku** pole. Pokud ovládací prvek dialogovém okně pole může obsahovat hodnotu, a pokud vyberete **hodnotu**, pak **typ proměnné** Určuje hodnotu, která může obsahovat řízení příslušného typu. V tématu [ovládací prvky dialogové okno a typy proměnných](../ide/dialog-box-controls-and-variable-types.md) Další informace.  
  
     Tato hodnota závisí na výběr v **ID ovládacího prvku** a nelze je změnit.  
  
 **Název proměnné**  
 Nastaví název členské proměnné, který chcete přidat. Členské proměnné obvykle začínají identifikační řetězec "m_", který je poskytnut pro vás ve výchozím nastavení.  
  
 **Proměnná ovládacího prvku**  
 Označuje, že členské proměnné spravuje ovládacího prvku v dialogovém okně s [výměny dat a ověření dat](../mfc/dialog-data-exchange-and-validation.md) podporovat. V tématu [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) Další informace. Tato možnost je dostupná pouze pro členské proměnné přidány do třídy odvozené od třídy [CDialog](../mfc/reference/cdialog-class.md). Toto pole chcete aktivovat **ID ovládacího prvku** a **řízení typu** možnosti.  
  
 **ID ovládacího prvku**  
 Nastaví ID pro proměnnou ovládací prvek, který chcete přidat. Vyberte ze seznamu ID pro typ ovládacího prvku, pro kterou přidáváte členské proměnné. Seznam je aktivní pouze tehdy, když **řídicí proměnná** políčko zaškrtnuto, a je omezen na ID pro ovládací prvky již přidán do dialogového okna. Například pro standardní **OK** je ID ovládacího prvku tlačítko **IDOK**.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Ovládací prvek**|Tato možnost nastavená ve výchozím nastavení pro typ ovládacího prvku. (Jak je můžete chtít provést v seznamu, pole se seznamem nebo upravit) spravuje ovládacího prvku sám a není stavu nebo obsah ovládacího prvku.|  
|**Hodnota**|Tato možnost je dostupná jenom pro typy ovládacích prvků, které mohou obsahovat hodnotu (například textové pole) nebo odpovídal stavu (například zaškrtávací políčko) a pro které může spravovat rozsah, obsah nebo stavu. V tématu [ovládací prvky dialogové okno a typy proměnných](../ide/dialog-box-controls-and-variable-types.md) Další informace.|  
  
 **Kategorie**  
 Určuje, jestli je proměnná založený na typu ovládacího prvku nebo hodnota ovládacího prvku.  
  
 **– Typ ovládacího prvku**  
 Nastaví typ ovládacího prvku, který chcete přidat. Toto políčko není možné změnit. Například tlačítko má typ ovládacího prvku **tlačítko**, a seznamem má typ ovládacího prvku **COMBOBOX**. V tématu [ovládací prvky dialogové okno a typy proměnných](../ide/dialog-box-controls-and-variable-types.md) Další informace.  
  
 **Maximální počet znaků**  
 K dispozici pouze tehdy, když **typ proměnné** je nastaven na [CString](../atl-mfc-shared/reference/cstringt-class.md). Určuje maximální počet znaků, které mohou být uloženy ovládacího prvku.  
  
 **Minimální hodnota**  
 K dispozici, pouze pokud je typ proměnné **BOOL**, `int`, **Celé_číslo**, **dlouho**, `DWORD`, **float**, **dvojité**, **BAJTŮ**, **krátké**, [COLECurrency](../mfc/reference/colecurrency-class.md) nebo [CTime –](../atl-mfc-shared/reference/ctime-class.md). Určuje nejnižší hodnotu přijatelné pro změnu nebo rozsah.  
  
 **Hodnota maximálního počtu**  
 K dispozici, pouze pokud je typ proměnné **BOOL**, `int`, **Celé_číslo**, **dlouho**, `DWORD`, **float**, **dvojité**, **BAJTŮ**, **krátké**, `COLECurrency` nebo `CTime`. Určuje nejvyšší hodnotu přijatelné pro změnu nebo rozsah.  
  
 **soubor h**  
 Pro ovládací prvky ActiveX, jejichž členské proměnné vyžadují obálkovou třídu. Nastaví název hlavičky souboru přidejte deklaraci třídy.  
  
 **souboru**  
 Pro ovládací prvky ActiveX, jejichž členské proměnné vyžadují obálkovou třídu. Nastaví název souboru implementace přidejte definici třídy.  
  
 **Komentář**  
 Komentář v záhlaví souboru pro členské proměnné.  
  
## <a name="see-also"></a>Viz také  
 [Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)