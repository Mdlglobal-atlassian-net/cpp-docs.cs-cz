---
title: "Vytvoření jednoduchého příjemce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5febdc019f5e575f685e4e93c892b7f5e777b776
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-simple-consumer"></a>Vytvoření jednoduchého příjemce
Pomocí Průvodce projektu knihovny ATL a průvodce příjemcem knihovny ATL technologie OLE DB vygenerujte příjemce technologie OLE DB šablony.  
  
#### <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>K vytvoření konzolové aplikace pro příjemce technologie OLE DB  
  
1.  Na **soubor** nabídky, klikněte na tlačítko **nový**a potom klikněte na **projektu**.  
  
     **Nový projekt** zobrazí se dialogové okno.  
  
2.  V podokně typy projektů, klikněte **projekty Visual C++** složku a pak klikněte na tlačítko **projektu Win32** ikona v podokně šablon. V **název** pole, zadejte název projektu, například **MyCons**.  
  
3.  Click **OK**.  
  
     Zobrazí se Průvodce projektem Win32.  
  
4.  Na **nastavení aplikace** vyberte **Konzolová aplikace**a potom vyberte **přidat podporu pro knihovny ATL**.  
  
5.  Klikněte na tlačítko **Dokončit** zavřete průvodce a vygenerování projektu.  
  
 Potom pomocí průvodce příjemcem knihovny ATL technologie OLE DB přidání objektu příjemce technologie OLE DB.  
  
#### <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Vytvoření příjemce pomocí průvodce příjemcem knihovny ATL technologie OLE DB  
  
1.  V zobrazení tříd, klikněte pravým tlačítkem `MyCons` projektu.  
  
2.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na **přidat třídu**.  
  
     **Přidat třídu** zobrazí se dialogové okno.  
  
3.  V podokně kategorie, klikněte na **Visual C++**, klikněte na tlačítko **ATL příjemce technologie OLE DB** v podokně šablon a pak klikněte na ikonu **otevřete**.  
  
     Zobrazí se průvodce příjemcem knihovny ATL technologie OLE DB.  
  
4.  Klikněte **zdroj dat** tlačítko.  
  
     **Vlastnosti propojení dat** zobrazí se dialogové okno.  
  
5.  V **vlastnosti propojení dat** dialogové okno pole, postupujte takto:  
  
    -   Na **zprostředkovatele** určete zprostředkovatele OLE DB.  
  
    -   Na **připojení** kartě, zadejte název serveru, přihlašovací ID a heslo pro zdroj dat a databáze na serveru.  
  
    > [!NOTE]
    >  Existuje problém zabezpečení s **povolit uložení hesla** funkce **vlastnosti propojení dat** dialogové okno. V **zadejte informace pro přihlášení k serveru**, existují dvě přepínací tlačítka: **integrované zabezpečení systému Windows NT použití** a **použít určité uživatelské jméno a heslo**.  
  
    > [!NOTE]
    >  Pokud vyberete **použít určité uživatelské jméno a heslo**, máte možnost uložení hesla (pomocí **povolit uložení hesla** políčko); však tato možnost není zabezpečený. Je vhodné vybrat **integrované zabezpečení systému Windows NT použití**; tato volba používá systém Windows NT ověřit vaši identitu.  
  
    > [!NOTE]
    >  Pokud nemůžete použít integrované zabezpečení Windows NT, měli byste použít aplikaci na střední vrstvě pro vyzvání uživatele k zadání hesla nebo k uložení hesla v umístění s mechanismy zabezpečení k ochraně jeho (místo ve zdrojovém kódu).  
  
     Po výběru zprostředkovatele a další nastavení, klikněte na tlačítko **Test připojení** ověření výběru z předchozích dialogové okno stránek. Pokud **výsledky** pole sestavy `Test connection succeeded`, klikněte na tlačítko **OK** k vytvoření propojení data.  
  
     **Vyberte objekt databáze** zobrazí se dialogové okno.  
  
6.  Vyberte tabulky, zobrazení nebo uložené proceduře pomocí ovládacího prvku strom. Pro účely tohoto postupu vyberte z databáze Northwind tabulky produktů.  
  
7.  Click **OK**. Vrátí průvodce příjemcem knihovny ATL technologie OLE DB.  
  
8.  Dokončení Průvodce názvy pro `Class` a **soubor h** na základě názvu tabulky a zobrazení nebo uložené procedury, kterou jste vybrali. Pokud chcete, můžete upravit tyto názvy.  
  
9. Vymazat **Attributed** políčko tak, aby průvodce vytvoří příjemce kódu pomocí [tříd šablon technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) místo výchozího [atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
10. V části **typ**, vyberte **příkaz**.  
  
     Průvodce vytvoří [CCommand](../../data/oledb/ccommand-class.md)– na základě příjemce, pokud vyberete **příkaz** nebo [CTable](../../data/oledb/ctable-class.md)– na základě příjemce, pokud vyberete **tabulky**. Třída tabulky nebo příkaz nazývá po vybraný objekt, ale můžete upravit název.  
  
11. V části **podporu**, ponechte **změnu**, **vložit**, a **odstranit** políčka prázdná.  
  
     Vyberte **změnu**, **vložit**, a **odstranit** zaškrtávací políčka pro podporu změn, vkládání a odstraňování záznamů v dané sadě řádků, pokud je to nutné. Další informace o zápisu dat do data ukládat najdete v tématu [aktualizace sad řádků](../../data/oledb/updating-rowsets.md).  
  
12. Klikněte na tlačítko **Dokončit** pro vytvoření příjemce.  
  
 Průvodce vytvoří příkaz třídy a třídy uživatelského záznamu, jak je znázorněno v [vygenerované třídy](../../data/oledb/consumer-wizard-generated-classes.md). Třída příkazu bude mít název, který jste zadali v `Class` pole v průvodci (v tomto případě `CProducts`), a třída uživatelského záznamu bude mít název ve tvaru "*ClassName*přistupujícího objektu" (v tomto případě `CProductsAccessor`).  
  
> [!NOTE]
>  Průvodce uloží do souboru Products.h následující řádek:  
  
```  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  Tento řádek brání aplikaci příjemce v kompilaci a upozorní, zkontrolujte připojovací řetězec pro pevně hesla. Po zkontrolování připojovací řetězec, můžete odebrat tento řádek kódu.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)