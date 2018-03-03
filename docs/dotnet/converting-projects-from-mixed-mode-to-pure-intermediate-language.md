---
title: "Převod projektů ze smíšeného režimu do čistého IL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- intermediate language, mixed-mode applications
- mixed-mode applications
- mixed-mode applications, intermediate language
- projects [C++], converting to intermediate language
ms.assetid: 855f9e3c-4f09-4bfe-8eab-a45f68292be9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0276d5b5420ed0294b2cf3438190f79d03585744
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="converting-projects-from-mixed-mode-to-pure-intermediate-language"></a>Převod projektů ze smíšeného režimu do čistého IL (Intermediate Language)
Všechny projekty Visual C++ CLR propojit běhové knihovny jazyka C ve výchozím nastavení. V důsledku toho jsou klasifikovány jako aplikace ve smíšeném režimu, proto, že kombinují nativní kód s kódem, který se zaměřuje modul common language runtime (spravovaný kód). Při kompilaci jsou, že se kompilují do převodní jazyk (IL), také známé jako Microsoft (MSIL intermediate language).  
  
### <a name="to-convert-your-mixed-mode-application-into-pure-intermediate-language"></a>K převedení aplikace ve smíšeném režimu do čistého IL  
  
1.  Odebrat odkazy na [běhové knihovny jazyka C](../c-runtime-library/crt-library-features.md) (CRT):  
  
    1.  V souboru definice vstupní bod aplikace, změňte vstupní bod do `Main()`. Pomocí `Main()` označuje, že projektu neobsahuje odkazy na CRT.  
  
    2.  V Průzkumníku řešení klikněte pravým tlačítkem na projekt a vyberte **vlastnosti** v místní nabídce k otevření stránek vlastností pro vaši aplikaci.  
  
    3.  V **Upřesnit** stránku vlastností projektu **Linkeru**, vyberte **vstupní bod** a pak zadejte **hlavní** v tomto poli.  
  
    4.  Pro konzolové aplikace v **systému** stránku vlastností projektu **Linkeru**, vyberte **subsystému** pole a změňte jej na **konzoly (/ Subsystem:Console)**.  
  
        > [!NOTE]
        >  Není nutné nastavit tuto vlastnost pro aplikace Windows Forms, protože **subsystému** je nastaveno na **systému Windows (nebo subsystému: WINDOWS)** ve výchozím nastavení.  
  
    5.  V souboru stdafx komentář všechny `#include` příkazy. Například v konzolové aplikace:  
  
        ```  
        // #include <iostream>  
        // #include <tchar.h>  
        ```  
  
         -nebo-  
  
         Například v aplikacích Windows Forms:  
  
        ```  
        // #include <stdlib.h>  
        // #include <malloc.h>  
        // #include <memory.h>  
        // #include <tchar.h>  
        ```  
  
    6.  Pro aplikace Windows Forms v souboru Form1.CPP příkaz Komentář `#include` příkaz odkazující na Windows. Příklad:  
  
        ```  
        // #include <windows.h>  
        ```  
  
2.  Přidejte následující kód do stdafx.h:  
  
    ```  
    #ifndef __FLTUSED__  
    #define __FLTUSED__  
       extern "C" __declspec(selectany) int _fltused=1;  
    #endif  
    ```  
  
3.  Odeberte všechny nespravované typy:  
  
    1.  Pokud je to vhodné, nahraďte nespravované typy odkazy na struktury z [systému](https://msdn.microsoft.com/en-us/library/system.appdomainmanager.appdomainmanager.aspx) oboru názvů. V následující tabulce jsou uvedeny běžné spravované typy:  
  
        |Struktura|Popis|  
        |---------------|-----------------|  
        |[Logická hodnota](https://msdn.microsoft.com/en-us/library/system.boolean\(v=vs.140\).aspx)|Představuje logickou hodnotu.|  
        |[Bajtů](https://msdn.microsoft.com/en-us/library/system.byte\(v=vs.140\).aspx)|Představuje 8bitové nepodepsanou celočíselnou hodnotu.|  
        |[Char –](https://msdn.microsoft.com/en-us/library/system.char\(v=vs.140\).aspx)|Představuje znak Unicode.|  
        |[Data a času](https://msdn.microsoft.com/en-us/library/system.datetime.datetime.aspx)|Představuje okamžik v čase, obvykle vyjádřený jako datum a čas, den.|  
        |[Decimal](https://msdn.microsoft.com/en-us/library/system.decimal\(v=vs.140\).aspx)|Představuje desetinné číslo.|  
        |[Double](https://msdn.microsoft.com/en-us/library/system.double\(v=vs.140\).aspx)|Představuje číslo s plovoucí desetinnou čárkou dvojitou přesností.|  
        |[Identifikátor GUID](https://msdn.microsoft.com/en-us/library/system.guid\(v=vs.140\).aspx)|Představuje globálně jedinečný identifikátor (GUID).|  
        |[Int16](https://msdn.microsoft.com/en-us/library/system.int16\(v=vs.140\).aspx)|Představuje 16bitové celé číslo se znaménkem.|  
        |[Int32](https://msdn.microsoft.com/en-us/library/system.int32\(v=vs.140\).aspx)|Představuje 32bitové celé číslo se znaménkem.|  
        |[Int64](https://msdn.microsoft.com/en-us/library/system.int64\(v=vs.140\).aspx)|Představuje 64bitové celé číslo se znaménkem.|  
        |[IntPtr](https://msdn.microsoft.com/en-us/library/system.intptr\(v=vs.140\).aspx)|Specifické pro platformu typ, který se používá k reprezentování ukazatel nebo popisovač.|  
        |[SByte –](https://msdn.microsoft.com/en-us/library/system.byte.aspx)|Představuje 8bitové znaménkem.|  
        |[Jeden](https://msdn.microsoft.com/en-us/library/system.single.aspx)|Představuje číslo s plovoucí desetinnou čárkou jednoduchou přesností.|  
        |[Časový interval](https://msdn.microsoft.com/en-us/library/system.timespan\(v=vs.140\).aspx)|Představuje časovém intervalu.|  
        |[UInt16](https://msdn.microsoft.com/en-us/library/system.uint16\(v=vs.140\).aspx)|Představuje celé číslo bez znaménka 16 bitů.|  
        |[UInt32](https://msdn.microsoft.com/en-us/library/system.uint32\(v=vs.140\).aspx)|Představuje 32bitové číslo bez znaménka.|  
        |[UInt64](https://msdn.microsoft.com/en-us/library/system.uint64\(v=vs.140\).aspx)|Představuje celé číslo bez znaménka 64-bit.|  
        |[UIntPtr](https://msdn.microsoft.com/en-us/library/system.uintptr\(v=vs.140\).aspx)|Specifické pro platformu typ, který se používá k reprezentování ukazatel nebo popisovač.|  
        |[Void](https://msdn.microsoft.com/en-us/library/system.void\(v=vs.140\).aspx)|Určuje metodu, která nevrátí hodnotu; To znamená že metoda má typ vrácené hodnoty void.|