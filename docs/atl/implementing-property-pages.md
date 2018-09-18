---
title: Implementace stránek vlastností | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IPropertyPage2 class
- IPropertyPage class
- property pages, implementing
ms.assetid: 62f29440-33a7-40eb-a1ef-3634c95f640c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f69dab9dfc9216d1c56ed54730d5f94cbb58b1db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088732"
---
# <a name="implementing-property-pages"></a>Implementace stránek vlastností

Stránky vlastností jsou objekty COM, které implementují `IPropertyPage` nebo `IPropertyPage2` rozhraní. Knihovna ATL poskytuje podporu pro implementace stránek vlastností prostřednictvím [Průvodce stránkou vlastností ATL](../atl/reference/atl-property-page-wizard.md) v [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md).

Chcete-li vytvořit pomocí knihovny ATL stránky vlastností:

- Vytvořte nebo otevřete projekt knihovny ATL dynamická knihovna (DLL) serveru.

- Otevřít [dialogové okno Přidat třídu](../ide/add-class-dialog-box.md) a vyberte **stránka vlastností knihovny ATL**.

- Ujistěte se, že vaše stránka vlastností objektu apartment vláken (protože má uživatelské rozhraní).

- Nastavte název, popis (řetězec Doc) a soubor nápovědy, který se má přidružit vaše stránky.

- Přidání ovládacích prvků do prostředku generované dialogového okna tak, aby fungoval jako uživatelského rozhraní stránky vlastností.

- Reakce na změny v uživatelském rozhraní na stránce provést ověření, aktualizujte stránku webu nebo aktualizovat objekty přidružené k vaší stránky. Konkrétně volat [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty) když uživatel provede změny na stránku vlastností.

- Volitelně můžete přepsat `IPropertyPageImpl` metod pomocí níže uvedených pokynů.

   |Ipropertypageimpl – metoda|Přepište, pokud chcete...|Poznámky|  
   |------------------------------|----------------------------------|-----------|  
   |[SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects)|Proveďte základní vhodnosti kontrol počet objektů, které jsou předávány na vaši stránku a rozhraní, které podporují.|Spuštění vlastního kódu před voláním implementaci základní třídy. Pokud objekty nastavování nevyhovují vašim požadavkům, by volání selhat co nejdřív.|  
   |[Aktivovat](../atl/reference/ipropertypageimpl-class.md#activate)|Inicializujte na stránce uživatelského rozhraní (třeba nastavit ovládací prvky dialogového okna s aktuální hodnoty vlastností z objektů, dynamicky vytvořit ovládací prvky nebo provést další inicializaci).|Volejte implementaci základní třídy před váš kód tak, aby základní třída má možnost vytvořit dialogové okno a všechny ovládací prvky před pokusem o je aktualizovat.|  
   |[Použít](../atl/reference/ipropertypageimpl-class.md#apply)|Ověřte nastavení vlastností a aktualizovat objekty.|Není nutné volat implementaci základní třídy, protože nedělá nic kromě trasování volání.|  
   |[Deaktivace](../atl/reference/ipropertypageimpl-class.md#deactivate)|Odstraňte položky týkající se oken.|Zničí implementaci základní třídy dialogových oken představující stránku vlastností. Pokud budete potřebovat k vyčištění před jeho zničení dialogových oken, měli byste přidat kódu před voláním metody základní třídy.|

Implementace stránky vlastností příklad naleznete v tématu [příklad: implementace stránky vlastností](../atl/example-implementing-a-property-page.md).

> [!NOTE]
> Pokud chcete na stránce vlastností hostitelské ovládací prvky ActiveX, bude nutné změnit odvození třídy generované v průvodci. Nahraďte **CDialogImpl\<CYourClass >** s **CAxDialogImpl\<CYourClass >** v seznamu základních tříd.

## <a name="see-also"></a>Viz také

[Stránky vlastností](../atl/atl-com-property-pages.md)<br/>
[Ukázka ATLPages](../visual-cpp-samples.md)
