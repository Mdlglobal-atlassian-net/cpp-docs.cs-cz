---
title: Rozdíly mezi prostředími Windows Forms – MFC programování | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], compared to MFC
ms.assetid: f3bfcf45-cfd4-45a4-8cde-5f4dbb18ee51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9ad9e47ba2bb3d9a5e5b21620a4bf4b50177d63b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="windows-formsmfc-programming-differences"></a>Rozdíly v programování mezi prostředími Windows Forms a MFC
Témata v [pomocí uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md) popisují Podpora MFC pro Windows Forms. Pokud nejste obeznámeni s rozhraní .NET Framework nebo programování MFC, toto téma obsahuje základní informace o programování rozdíly mezi nimi.  
  
 Windows Forms je pro vytváření aplikací pro Microsoft Windows na rozhraní .NET Framework. Toto rozhraní poskytuje moderní, objektově orientovaný, rozšiřitelnou sadu tříd, které vám umožní vyvíjet bohaté aplikace pro systém Windows. S Windows Forms budete moci vytvořit aplikaci rich client, která můžete přístup k široké škály zdrojů dat a poskytnout dat zobrazení a úpravy dat zařízení pomocí Windows Forms – ovládací prvky.  
  
 Ale pokud jste zvyklí MFC, které lze použít pro vytváření určitých typů aplikací, které ještě nejsou výslovně podporovány v systému Windows Forms. Dialogové okno aplikace MFC odpovídají formulářových aplikací Windows. Ale neposkytují infrastrukturu tak, aby přímo podporují jinými typy aplikací MFC dokumentu OLE server/kontejner, dokumenty ActiveX, Document/View – podpora pro jeden dokument (SDI rozhraní), rozhraní více dokumentů (MDI), a více rozhraní nejvyšší úrovně (MTI). Můžete napsat vlastní logiky k vytváření těchto aplikací.  
  
 Další informace o aplikacích Windows Forms najdete v tématu [Úvod do Windows Forms](/dotnet/framework/winforms/windows-forms-overview).  
  
 Ukázkové aplikace, která ukazuje použití MFC modelu Windows Forms, najdete v části [integrace produktů Windows Forms a MFC](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en).  
  
 Následující zobrazení MFC nebo dokumentu a vlastnosti příkazu směrování nemají ekvivalent v systému Windows Forms:  
  
-   Integrace prostředí  
  
     Knihovna MFC zpracovává příkazů dynamická data systému exchange (DDE) a argumenty příkazového řádku, které používá prostředí, když klikněte pravým tlačítkem na dokument a vyberte tyto příkazy jako otevřít, upravit nebo vytisknout. Windows Forms nemá integraci prostředí a neodpoví na příkazy prostředí.  
  
-   Šablony dokumentů  
  
     V prostředí MFC přidružte šablony dokumentů zobrazení, které jsou obsaženy v okně s rámečkem (v režimu MDI, SDI nebo MTI), dokument, který jste otevřeli. Windows Forms nemá žádný ekvivalent šablony dokumentů.  
  
-   Dokumenty  
  
     MFC registruje typy souborů dokumentu a zpracuje typu dokumentu, při otevření dokumentu z prostředí. Windows Forms nemá žádný dokument podpory.  
  
-   Stavy dokumentu  
  
     MFC udržuje nevyřízené stavy pro dokument. Proto když zavřete aplikaci, zavřete poslední zobrazení, která obsahuje aplikaci nebo ukončení ze systému Windows, MFC vás vyzve k uložení dokumentů. Windows Forms má ekvivalentní nepodporuje.  
  
-   Příkazy  
  
     MFC má koncept příkazů. Panel nabídek, nástrojů a místní nabídky můžete vyvolat všechny stejný příkaz, například vyjmutí a kopírování. V systému Windows Forms jsou příkazy těsně vázaných událostí z konkrétní prvek uživatelského rozhraní (například položku nabídky); Proto musíte explicitně přidat všechny události příkaz. Můžete také zpracování více událostí pomocí jedné obslužné rutiny ve Windows Forms. Další informace najdete v tématu [připojení více událostí k jedné obslužné rutině událostí ve Windows Forms](/dotnet/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms).  
  
-   Směrování příkazů  
  
     Směrování příkazů MFC umožňuje aktivní zobrazení nebo dokument k příkazům procesu. Vzhledem k tomu, že stejný příkaz často má odlišný význam pro různá zobrazení (například kopírování odlišné chování textového zobrazení upravit než v editoru grafiky), příkazy muset zpracovávat aktivního zobrazení. Protože Windows Forms nabídek a panelů nástrojů nemají žádné podstatné porozumění aktivního zobrazení, nemůže mít jinou obslužnou rutinu pro každý typ zobrazení pro vaše **MenuItem.Click** události bez nutnosti psaní kódu Další interní.  
  
-   Příkaz update mechanismus  
  
     MFC má příkaz aktualizačního mechanismu. Proto je zodpovědný za stav prvky uživatelského rozhraní (například povolování nebo zakazování tlačítka s nabídkou položky nebo nástroj a zkontrolovat stav) aktivní zobrazení nebo dokumentu. Windows Forms nemá žádný ekvivalent mechanismus příkazu update.  
  
## <a name="see-also"></a>Viz také  
 [Použití uživatelského ovládacího prvku Windows Form v prostředí MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)   
 [Windows Forms návody](http://msdn.microsoft.com/en-us/fd44d13d-4733-416f-aefc-32592e59e5d9)