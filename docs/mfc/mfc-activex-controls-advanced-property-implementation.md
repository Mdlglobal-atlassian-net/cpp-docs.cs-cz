---
title: "Ovládací prvky MFC ActiveX: Rozšířené implementace vlastností | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 239905a6a1943e923fc64740e840027388dbbc61
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC – ovládací prvky ActiveX: Implementace rozšířených vlastností
Tento článek popisuje témata týkající se implementace rozšířené vlastnosti v ovládacím prvku ActiveX:  
  
-   [Vlastnosti jen pro čtení a jen pro zápis](#_core_read2donly_and_write2donly_properties)  
  
-   [Vrácení chybových kódů z vlastnosti](#_core_returning_error_codes_from_a_property)  
  
##  <a name="_core_read2donly_and_write2donly_properties"></a>Vlastnosti jen pro čtení a jen pro zápis  
 Průvodce přidáním vlastnosti poskytuje rychlý a snadný metody k implementaci vlastnosti jen pro čtení, nebo jen pro zápis pro ovládací prvek.  
  
#### <a name="to-implement-a-read-only-or-write-only-property"></a>K implementaci vlastnosti jen pro čtení nebo jen pro zápis  
  
1.  Načtení projektu ovládacího prvku.  
  
2.  V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.  
  
3.  Klikněte pravým tlačítkem na uzel rozhraní pro vlastní ovládací prvek (druhého uzlu uzlu knihovny) a místní nabídce.  
  
4.  V místní nabídce klikněte na **přidat** a pak klikněte na **přidat vlastnost**.  
  
     Tím se otevře [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md).  
  
5.  V **název vlastnosti** zadejte název vaší vlastnosti.  
  
6.  Pro **typem implementace**, klikněte na tlačítko **metody Get/Set**.  
  
7.  V **typ vlastnosti** vyberte správný typ vlastnosti.  
  
8.  Pokud chcete vlastnost určenou jen pro čtení, vymažte název funkce sady. Pokud chcete vlastnost jen pro zápis, vymažte název funkce Get.  
  
9. Klikněte na tlačítko **Dokončit**.  
  
 Když to uděláte, Průvodce přidáním vlastnosti vloží funkci `SetNotSupported` nebo `GetNotSupported` v položce mapy odesílání místo normální nastavit nebo získat funkce.  
  
 Pokud chcete změnit existující vlastnosti jen pro čtení nebo jen pro zápis, můžete upravit mapy odesílání ručně a odeberte nepotřebné sady nebo Get funkci ze třídy control.  
  
 Pokud chcete vlastnost, která má být podmíněně jen pro čtení nebo jen pro zápis (například jenom v případě, že vlastní ovládací prvek pracuje v určitém režimu), můžete poskytovat funkci Set nebo Get jako normální a volání `SetNotSupported` nebo `GetNotSupported` fungovat, kde je to vhodné. Příklad:  
  
 [!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]  
  
 Tato ukázka kódu volá `SetNotSupported` Pokud `m_bReadOnlyMode` – datový člen je **TRUE**. Pokud **FALSE**, pak je vlastnost nastavena na novou hodnotu.  
  
##  <a name="_core_returning_error_codes_from_a_property"></a>Vrácení chybových kódů z vlastnosti  
 K označení, že došlo k chybě při pokusu o získání nebo nastavení vlastnosti, použijte `COleControl::ThrowError` funkce, který přebírá `SCODE` (kód stavu) jako parametr. Můžete použít i předdefinovanou `SCODE` nebo definovat vlastní. Seznam předdefinovaných `SCODE`s a pokyny k definování vlastní `SCODE`s, najdete v části [zpracování chyb v vaše ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX článek: Advanced témata.  
  
 Podpůrné funkce pro nejběžnější předdefinované neexistují `SCODE`s, jako například [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), a [COleControl:: SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).  
  
> [!NOTE]
>  `ThrowError`měl by být použit pouze jako způsob vrátila chybu z v rámci Get vlastnost nebo sadu funkci nebo metodu automatizace. Toto jsou jediné pokusů, které obslužná rutina příslušné výjimky bude k dispozici v zásobníku.  
  
 Další informace o vytváření sestav výjimky v jiných oblastech kódu najdete v tématu [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) a v části [zpracování chyb v vaše ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v článku – ovládací prvky ActiveX: Upřesnit Témata.  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [MFC – ovládací prvky ActiveX: vlastnosti](../mfc/mfc-activex-controls-properties.md)   
 [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [COleControl – třída](../mfc/reference/colecontrol-class.md)
