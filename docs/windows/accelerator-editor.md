---
title: Editor akcelerátorů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.accelerator.F1
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [Visual Studio], accelerator key
- accelerator keys
- resource editors, Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- Accelerator editor
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0aed7c8ef617152144bbe211f83f442fe93d525e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648282"
---
# <a name="accelerator-editor"></a>Editor akcelerátorů
Tabulky akcelerátorů je prostředek Windows, který obsahuje seznam klávesy akcelerátoru (označované také jako klávesové zkratky) a identifikátory příkazů, které jsou s nimi spojeny. Program může mít více než jedné tabulky akcelerátoru.  
  
 Za normálních okolností akcelerátorů jsou použity jako klávesové zkratky pro příkazy programu, které jsou dostupné také na nabídku nebo panel nástrojů. Můžete však použít tabulky akcelerátorů k definování kombinace kláves pro příkazy, které nemají objekt uživatelského rozhraní k nim má přiřazené.  
  
 Můžete použít [zobrazení tříd](http://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925) připojit klíče příkazy akcelerátoru ke kódu.  
  
 S **akcelerátoru** editoru, můžete:  
  
-   [Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)  
  
-   [Přiřazení klíče akcelerátoru k položce nabídky](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [Úprava tabulek akcelerátorů](../windows/editing-accelerator-tables.md)  
  
-   [Pomocí předdefinované klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  Při použití **akcelerátoru** editoru, kliknete pravým tlačítkem na Zobrazit místní nabídku s často používanými příkazy. Dostupné příkazy závisí na ukazatel odkazuje na.  
  
    > [!NOTE]
    >  Windows neumožňuje vytvářet tabulky prázdný akcelerátoru. Pokud jste se žádné položky tabulky akcelerátorů, je odstraněn automaticky při ukládání tabulky.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)