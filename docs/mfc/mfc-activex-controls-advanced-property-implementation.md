---
title: 'Ovládací prvky MFC ActiveX: Pokročilé implementace vlastností | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], error codes
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
ms.assetid: ec2e6759-5a8e-41d8-a275-99af8ff6f32e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f18d9466c1608742f63e68caa639c1ad6697df1c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063650"
---
# <a name="mfc-activex-controls-advanced-property-implementation"></a>MFC – ovládací prvky ActiveX: Implementace rozšířených vlastností

Tento článek popisuje témat souvisejících s implementací rozšířené vlastnosti v ovládacím prvku ActiveX.

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být používána při novém vývoji. Další informace o moderních technologií, které nahrazují ActiveX naleznete v tématu [ovládací prvky ActiveX](activex-controls.md).

- [Vlastnosti jen pro čtení a jen pro zápis](#_core_read2donly_and_write2donly_properties)

- [Vrácení chybových kódů z vlastnosti](#_core_returning_error_codes_from_a_property)

##  <a name="_core_read2donly_and_write2donly_properties"></a> Vlastnosti jen pro čtení a jen pro zápis

Průvodce přidáním vlastnosti způsobem rychle a snadno implementovat jen pro čtení nebo jen pro zápis vlastnosti ovládacího prvku.

#### <a name="to-implement-a-read-only-or-write-only-property"></a>Implementace vlastnosti jen pro čtení nebo jen pro zápis

1. Načtení projektu ovládacího prvku.

1. V zobrazení tříd rozbalte uzel knihovny ovládacího prvku.

1. Klikněte pravým tlačítkem na uzel rozhraní pro ovládací prvek (druhý uzel uzlu knihovny) otevřete místní nabídku.

1. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat vlastnost**.

   Tím se otevře [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md).

1. V **název vlastnosti** zadejte název vašeho vlastnosti.

1. Pro **typ implementace**, klikněte na tlačítko **metody Get/Set**.

1. V **typ vlastnosti** vyberte správný typ pro vlastnost.

1. Pokud chcete vlastnost jen pro čtení, vymažte název funkce Set. Pokud chcete vlastnost jen pro zápis, vymažte název funkce Get.

9. Klikněte na tlačítko **Dokončit**.

Když toto provedete, Průvodce přidáním vlastnosti vloží funkci `SetNotSupported` nebo `GetNotSupported` v položce mapy odbavení místo normální nastavit nebo získat funkce.

Pokud chcete změnit existující vlastnosti jen pro čtení nebo jen pro zápis, můžete ručně upravit mapa odbavení a odeberte nepotřebné funkci Set nebo Get ze třídy control.

Pokud chcete vlastnost, která má být podmíněně jen pro čtení nebo jen pro zápis (například pouze v případě, že ovládací prvek funguje v určitém režimu), můžete poskytnout funkci Set nebo Get jako za normálních okolností a volat `SetNotSupported` nebo `GetNotSupported` funkce, kde je to vhodné. Příklad:

[!code-cpp[NVC_MFC_AxUI#29](../mfc/codesnippet/cpp/mfc-activex-controls-advanced-property-implementation_1.cpp)]

Tento vzorový kód volá `SetNotSupported` Pokud `m_bReadOnlyMode` je datový člen **TRUE**. Pokud **FALSE**, pak je nastavena na novou hodnotu.

##  <a name="_core_returning_error_codes_from_a_property"></a> Vrácení chybových kódů z vlastnosti

Chcete-li označit, že došlo k chybě při pokusu o získání nebo nastavení vlastnosti, použijte `COleControl::ThrowError` funkce, která přebírá SCODE (stavový kód) jako parametr. Můžete použít předdefinované SCODE nebo definovat svůj vlastní. Seznam předdefinovaných SCODEs a pokyny k definování vlastní SCODEs najdete v tématu [zpracování chyb v svůj ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v ovládacích prvcích ActiveX článku: Advanced témata.

Neexistuje pomocné funkce, nejběžnější předdefinované SCODEs, jako například [COleControl::SetNotSupported](../mfc/reference/colecontrol-class.md#setnotsupported), [COleControl::GetNotSupported](../mfc/reference/colecontrol-class.md#getnotsupported), a [COleControl::SetNotPermitted](../mfc/reference/colecontrol-class.md#setnotpermitted).

> [!NOTE]
>  `ThrowError` je určen pro použití pouze jako způsob vrátit chybu z v rámci vlastnosti Get nebo Set funkci nebo metodu služby automation. Jedná se o jediný případů, kdy se obslužná rutina příslušné výjimky budou k dispozici v zásobníku.

Další informace o vytváření sestav výjimky v jiných oblastech kód, naleznete v tématu [COleControl::FireError](../mfc/reference/colecontrol-class.md#fireerror) a v části [zpracování chyb v svůj ovládací prvek ActiveX](../mfc/mfc-activex-controls-advanced-topics.md) v následujícím článku – ovládací prvky ActiveX: Upřesnit Témata.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Vlastnosti](../mfc/mfc-activex-controls-properties.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl – třída](../mfc/reference/colecontrol-class.md)
