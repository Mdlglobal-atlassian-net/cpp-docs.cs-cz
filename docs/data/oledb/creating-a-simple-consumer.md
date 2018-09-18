---
title: Vytvoření jednoduchého příjemce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 091a529bdd8eb80158fc093fd450e496bc4f18c2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052345"
---
# <a name="creating-a-simple-consumer"></a>Vytvoření jednoduchého příjemce

Generování šablony příjemce OLE DB pomocí Průvodce projektem ATL a průvodce příjemcem ATL OLE DB.  
  
### <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>K vytvoření konzolové aplikace pro příjemce technologie OLE DB  
  
1. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
1. V podokně typy projektů, klikněte **projekty Visual C++** složku a pak klikněte na tlačítko **projekt Win32** ikony v podokně šablon. V **název** zadejte název projektu, například **MyCons**.  
  
1. Klikněte na tlačítko **OK**.  
  
     Zobrazí se Průvodce projektu Win32.  
  
1. Na **nastavení aplikace** stránce **konzolovou aplikaci**a pak vyberte **přidat podporu ATL**.  
  
1. Klikněte na tlačítko **Dokončit** zavřete průvodce a generování projektu.  
  
Pak přidejte objekt příjemce technologie OLE DB pomocí průvodce příjemcem ATL OLE DB.  
  
#### <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Vytvoření příjemce pomocí průvodce příjemcem ATL OLE DB  
  
1. V zobrazení tříd klikněte pravým tlačítkem myši `MyCons` projektu.  
  
1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.  
  
     **Přidat třídu** zobrazí se dialogové okno.  
  
1. V podokně kategorie, klikněte na tlačítko **Visual C++**, klikněte na tlačítko **příjemce ATL OLE DB** v podokně šablon a pak klikněte na ikonu **otevřít**.  
  
     Zobrazí se průvodce příjemcem ATL OLE DB.  
  
1. Klikněte na tlačítko **zdroj dat** tlačítko.  
  
     **Vlastnosti propojení dat** zobrazí se dialogové okno.  
  
1. V **vlastnosti propojení dat** dialogové okno pole, postupujte takto:  
  
    -   Na **poskytovatele** kartu, zadejte zprostředkovatele OLE DB.  
  
    -   Na **připojení** kartu, zadejte název serveru, přihlašovací jméno a heslo pro zdroj dat a databáze na serveru.  
  
    > [!NOTE]
    >  Existuje problém zabezpečení s **povolit uložení hesla** funkce **vlastnosti propojení dat** dialogové okno. V **zadejte informace pro přihlášení k serveru**, existují dva přepínače: **integrované zabezpečení Windows NT použití** a **použít konkrétní uživatelské jméno a heslo**.  
  
    > [!NOTE]
    >  Pokud vyberete **použít konkrétní uživatelské jméno a heslo**, máte možnost uložení hesla (pomocí **povolit uložení hesla** zaškrtávací políčko), ale tato možnost není zabezpečený. Doporučuje se, že vyberete **integrované zabezpečení Windows NT použití**; tato možnost používá k ověření vaší identity systému Windows NT.  
  
    > [!NOTE]
    >  Pokud nemůžete použít Windows NT integrované zabezpečení, používejte aplikace střední vrstvy vyzvat uživatele k zadání hesla nebo k uložení hesla v umístění s mechanismy zabezpečení, které zvýší jeho ochranu (místo ve zdrojovém kódu).  
  
     Po výběru poskytovatele a další nastavení, klikněte na **Test připojení** ověření výběru z předchozího stránek dialogového okna. Pokud **výsledky** pole sestavy `Test connection succeeded`, klikněte na tlačítko **OK** pro vytvoření odkazu data.  
  
     **Vyberte databázový objekt** zobrazí se dialogové okno.  
  
1. Výběr tabulky, zobrazení nebo uložené procedury pomocí ovládacího prvku stromu. Pro účely tohoto postupu vyberte tabulku produktů z databáze Northwind.  
  
1. Klikněte na tlačítko **OK**. Vrátí průvodce příjemcem ATL OLE DB.  
  
1. Názvy pro dokončení průvodce `Class` a **souboru .h** na základě názvu tabulky, zobrazení nebo uložené procedury, kterou jste vybrali. Pokud chcete, můžete upravit tyto názvy.  
  
9. Zrušte **Atributovaný** zaškrtněte políčko, aby průvodce vytvoří příjemce kódu pomocí [tříd šablon technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) místo výchozího [atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
10. V části **typ**vyberte **příkaz**.  
  
     Průvodce vytvoří [CCommand](../../data/oledb/ccommand-class.md)– na základě uživatelů, pokud vyberete **příkaz** nebo [CTable](../../data/oledb/ctable-class.md)– na základě uživatelů, pokud vyberete **tabulky**. Vybraný objekt má stejný název třídy příkazu nebo tabulky, ale můžete upravit název.  
  
11. V části **podporu**, nechat **změnu**, **vložit**, a **odstranit** políčka prázdná.  
  
     Vyberte **změnu**, **vložit**, a **odstranit** zaškrtávací políčka pro podporu změn, vkládání a odstraňování záznamů v dané sadě řádků, pokud je to nutné. Další informace o zápisu dat do dat úložiště, najdete v článku [aktualizace sad řádků](../../data/oledb/updating-rowsets.md).  
  
12. Klikněte na tlačítko **Dokončit** vytvořte příjemce.  
  
Průvodce vygeneruje třídu příkazu nebo třída záznamů uživatelů, jak je znázorněno v [vygenerované třídy](../../data/oledb/consumer-wizard-generated-classes.md). Třídy příkazů bude mít název, který jste zadali v `Class` pole v průvodci (v tomto případě `CProducts`), a třídu záznamů uživatele bude mít název ve tvaru "*ClassName*přístupového objektu" (v tomto případě `CProductsAccessor`).  
  
> [!NOTE]
>  Průvodce umístí do souboru Products.h následující řádek:  
  
```cpp  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  Tento řádek znemožňuje spotřebitele aplikaci v kompilaci a vám připomene zkontrolovat pevně kódovaná hesla v připojovacím řetězci. Po kontrole připojovací řetězec, můžete odebrat tento řádek kódu.  
  
## <a name="see-also"></a>Viz také  

[Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)