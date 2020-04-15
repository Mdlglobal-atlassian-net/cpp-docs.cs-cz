---
title: 'MFC – ovládací prvky ActiveX: Distribuce ovládacích prvků ActiveX'
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
ms.openlocfilehash: 1ada1c801b2d9d62f1cc4cd5bf72a2995225b3de
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364616"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC – ovládací prvky ActiveX: Distribuce ovládacích prvků ActiveX

Tento článek popisuje několik problémů souvisejících s redistribucí ovládacích prvků ActiveX:

- [Verze ovládacího prvku ANSI nebo Unicode](#_core_ansi_or_unicode_control_versions)

- [Instalace ovládacích prvků ActiveX a redistribuovatelných knihoven DLL](#_core_installing_activex_controls_and_redistributable_dlls)

- [Registrace ovládacích prvků](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX je starší technologie, která by neměla být použita pro nový vývoj. Další informace o moderních technologiích, které nahrazují ovládací prvky ActiveX, naleznete [v tématu ActiveX Controls](activex-controls.md).

## <a name="ansi-or-unicode-control-versions"></a><a name="_core_ansi_or_unicode_control_versions"></a>Verze ovládacího prvku ANSI nebo Unicode

Musíte se rozhodnout, zda chcete dobýt verzi ovládacího prvku ANSI nebo Unicode nebo obojí. Toto rozhodnutí je založeno na faktorech přenositelnosti, které jsou vlastní znakovým množitelským mnostvím ANSI a Unicode.

Ovládací prvky ANSI, které fungují na všech operačních systémech Win32, umožňují maximální přenositelnost mezi různými operačními systémy Win32. Ovládací prvky Unicode fungují pouze v systému Windows NT (verze 3.51 nebo novější), nikoli však v systému Windows 95 nebo Windows 98. Pokud je přenositelnost vaším hlavním zájmem, dodejte ovládací prvky ANSI. Pokud budou ovládací prvky spuštěny pouze v systému Windows NT, můžete doručovat ovládací prvky Unicode. Můžete také zvolit odeslání obou a nechat aplikaci nainstalovat verzi nejvhodnější pro operační systém uživatele.

## <a name="installing-activex-controls-and-redistributable-dlls"></a><a name="_core_installing_activex_controls_and_redistributable_dlls"></a>Instalace ovládacích prvků ActiveX a redistribuovatelných knihoven DLL

Instalační program, který poskytujete s ovládacími prvky ActiveX, by měl vytvořit speciální podadresář adresáře systému Windows a nainstalovat ovládací prvky. OCX soubory v něm.

> [!NOTE]
> Pomocí rozhraní `GetWindowsDirectory` API systému Windows v instalačním programu získáte název adresáře systému Windows. Název podadresáře můžete odvodit z názvu vaší společnosti nebo produktu.

Instalační program musí nainstalovat potřebné redistribuovatelné soubory DLL do systémového adresáře systému Windows. Pokud některý z knihoven DLL jsou již k dispozici v počítači uživatele, instalační program by měl porovnat jejich verze s verzemi, které instalujete. Přeinstalujte soubor pouze v případě, že je číslo jeho verze vyšší než již nainstalovaný soubor.

Vzhledem k tomu, že ovládací prvky ActiveX lze použít pouze v aplikacích kontejneru OLE, není nutné distribuovat úplnou sadu knihoven OLE s ovládacími prvky. Můžete předpokládat, že obsahující aplikace (nebo samotný operační systém) má nainstalovány standardní knihovny OLE.

## <a name="registering-controls"></a><a name="_core_registering_controls"></a>Registrace ovládacích prvků

Před použitím ovládacího prvku je nutné pro něj vytvořit příslušné položky v registrační databázi systému Windows. Některé kontejnery ovládacích prvků ActiveX poskytují uživatelům položku nabídky k registraci nových ovládacích prvků, ale tato funkce nemusí být k dispozici ve všech kontejnerech. Proto můžete chtít instalační program zaregistrovat ovládací prvky při jejich instalaci.

Pokud chcete, můžete napsat instalační program a zaregistrovat ovládací prvek přímo.

Pomocí `LoadLibrary` rozhraní API systému Windows načtěte řídicí dll. Dále použijte `GetProcAddress` k získání adresy funkce "DllRegisterServer". Nakonec zavolejte `DllRegisterServer` funkci. Následující ukázka kódu ukazuje jednu `hLib` možnou metodu, kde `lpDllEntryPoint` ukládá popisovač knihovny ovládacích prvků a ukládá adresu funkce "DllRegisterServer".

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

Výhodou registrace ovládacího prvku přímo je, že není nutné vyvolat a načíst samostatný proces (konkrétně REGSVR32), což snižuje dobu instalace. Navíc vzhledem k tomu, že registrace je interní proces, instalační program dokáže zpracovat chyby a nepředvídané situace lépe než externí proces.

> [!NOTE]
> Před instalací instalačního programu ovládacího prvku `OleInitialize`ActiveX by měl volat . Po dokončení instalačního programu `OleUnitialize`volejte . Tím zajistíte, že knihovny DLL systému OLE jsou ve správném stavu pro registraci ovládacího prvku ActiveX.

MFCx0.DLL byste měli zaregistrovat.

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
