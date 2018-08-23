---
title: Získání ukazatelů do vyrovnávací paměti dat (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: db4f9370-dd95-4896-b5b8-4b202284f579
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87b95044c3a0b874d155b227db736c5e4b81f1b1
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613027"
---
# <a name="obtaining-pointers-to-data-buffers-ccx"></a>Získání ukazatelů do vyrovnávací paměti dat (C + +/ CX)
V modulu Windows Runtime [Windows::Storage::Streams::IBuffer](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ibuffer.aspx) rozhraní poskytuje jazykově neutrální, základem je stream znamená, že přístup k datové vyrovnávací paměti. V jazyce C++ můžete získat nezpracovaný ukazatel na podkladové pole bajtů s použitím rozhraní IBufferByteAccess knihovna Windows Runtime, který je definován v robuffer.h. Pomocí tohoto přístupu můžete upravit bajtové pole na místě přitom všechny nepotřebné kopie data.  
  
 Následující diagram znázorňuje obrázek prvek XAML, jejichž zdrojem je [Windows::UI::Xaml::Media::Imaging WriteableBitmap](http://msdn.microsoft.com/%20library/windows/apps/windows.ui.xaml.media.imaging.writeablebitmap.aspx). Klientskou aplikaci, která je napsána v libovolném jazyce můžete předat odkaz na `WriteableBitmap` c++ kódu a pak C++ pomocí odkazu zobrazíte na základní vyrovnávací paměti. V aplikaci univerzální platformy Windows, která je napsána v jazyce C++ můžete použít funkci v následujícím příkladu přímo ve zdrojovém kódu bez balení v součásti prostředí Windows Runtime.  
  
 ![C&#43; &#43; kód přímo přístup k datům pixel](../cppcx/media/ibufferbyteaccessdiagram.png "IBufferByteAccessDiagram")  
  
## <a name="getpointertopixeldata"></a>GetPointerToPixelData  
 Následující metoda přijímá [Windows::Storage::Streams::IBuffer](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ibuffer.aspx) a vrátí ukazatel raw k podkladové pole bajtů. Pro volání funkce, předejte [WriteableBitmap::PixelBuffer](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.imaging.writeablebitmap.pixelbuffer.aspx) vlastnost.  
  
```  
  
#include <wrl.h>  
#include <robuffer.h>  
using namespace Windows::Storage::Streams;  
using namespace Microsoft::WRL;  
typedef uint8 byte;  
// Retrieves the raw pixel data from the provided IBuffer object.  
// Warning: The lifetime of the returned buffer is controlled by  
// the lifetime of the buffer object that's passed to this method.  
// When the buffer has been released, the pointer becomes invalid  
// and must not be used.  
byte* Class1::GetPointerToPixelData(IBuffer^ pixelBuffer, unsigned int *length)  
{  
    if (length != nullptr)  
    {  
        *length = pixelBuffer ->Length;  
    }  
    // Query the IBufferByteAccess interface.  
    ComPtr<IBufferByteAccess> bufferByteAccess;  
    reinterpret_cast<IInspectable*>( pixelBuffer)->QueryInterface(IID_PPV_ARGS(&bufferByteAccess));  
  
    // Retrieve the buffer data.  
    byte* pixels = nullptr;  
    bufferByteAccess->Buffer(&pixels);  
    return pixels;  
}  
```  
  
## <a name="complete-example"></a>Kompletní příklad  
 Následující kroky ukazují, jak vytvořit aplikace s C# Universal Windows Platform, který předá `WriteableBitmap` ke komponentě ve C++ Windows Runtime knihovny DLL. Kód jazyka C++ získá ukazatel do vyrovnávací paměti pixelů a provádí jednoduchých úprav na místě v imagi. Jako alternativu můžete vytvořit klientskou aplikaci v jazyce Visual Basic, JavaScriptu nebo C++ místo C#. Pokud používáte C++, není nutné komponentu knihovny DLL; Tyto metody můžete přidat jenom přímo do třídy MainPage nebo jiné třídy, které definujete.  
  
#### <a name="create-the-client"></a>Vytvoření klienta  
  
1.  Použijte šablonu projektu prázdnou aplikaci pro vytvoření aplikace v jazyce C# Universal Windows Platform.  
  
2.  V souboru MainPage.xaml  
  
    -   Použít tento XAML k nahrazení `Grid` element:  
  
        ```cpp  
        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">  
                <StackPanel HorizontalAlignment="Left" Margin="176,110,0,0" VerticalAlignment="Top" Width="932">  
                    <Image x:Name="Pic"/>  
                    <Button Content="Process Image" HorizontalAlignment="Stretch" VerticalAlignment="Stretch" Height="47" Click="Button_Click_1"/>  
                </StackPanel>  
            </Grid>  
        ```  
  
3.  V MainPage.xaml.cs  
  
    1.  Přidejte tyto deklarace oboru názvů:  
  
        ```  
        using Windows.Storage;  
        using Windows.Storage.FileProperties;  
        using Windows.UI.Xaml.Media.Imaging;  
        using Windows.Storage.Streams;  
        using Windows.Storage.Pickers;  
        ```  
  
    2.  Přidat `WriteableBitmap` členské proměnné `MainPage` třídy a pojmenujte ho `m_bm`.  
  
        ```  
        private WriteableBitmap m_bm;  
        ```  
  
    3.  Použijte následující kód k nahrazení `OnNavigatedTo` pahýl metody. Otevře se okno pro výběr souboru při spuštění aplikace. (Všimněte si, že `async` – klíčové slovo se přidá k signatuře funkce).  
  
        ```c#  
        async protected override void OnNavigatedTo(NavigationEventArgs e)  
                {  
                    FileOpenPicker openPicker = new FileOpenPicker();  
                    openPicker.ViewMode = PickerViewMode.Thumbnail;  
                    openPicker.SuggestedStartLocation = PickerLocationId.PicturesLibrary;  
                    openPicker.FileTypeFilter.Add(".jpg");  
                    openPicker.FileTypeFilter.Add(".jpeg");  
                    openPicker.FileTypeFilter.Add(".png");  
  
                    StorageFile file = await openPicker.PickSingleFileAsync();  
                    if (file != null)  
                    {  
                        // Get the size of the image for the WriteableBitmap constructor.  
                        ImageProperties props = await file.Properties.GetImagePropertiesAsync();  
                        m_bm = new WriteableBitmap((int)props.Height, (int)props.Width);  
                        m_bm.SetSource(await file.OpenReadAsync());  
                        Pic.Source = m_bm;  
                    }  
                    else  
                    {  
                      //  Handle error...  
                    }  
                }  
        ```  
  
    4.  Přidáte obslužnou rutinu události pro kliknutí na tlačítko. (Protože `ImageManipCPP` nebyl vytvořen odkaz na obor názvů, ale může mít podtržení vlnovkou v okně editoru.)  
  
        ```  
        async private void Button_Click_1(object sender, RoutedEventArgs e)  
                {  
                    ImageManipCPP.Class1 obj = new ImageManipCPP.Class1();  
                    await obj.Negativize(m_bm);  
                    Pic.Source = m_bm;  
                }  
        ```  
  
#### <a name="create-the-c-component"></a>Vytvořit komponentu C++  
  
1.  Přidat novou součást modulu Windows Runtime C++ do stávajícího řešení a pojmenujte ho `ImageManipCPP`. Přidejte na ni odkaz v projektu C# kliknutím pravým tlačítkem na tento projekt v **Průzkumníka řešení** a zvolíte **přidat**, **odkaz**.  
  
2.  V Class1.h  
  
    1.  Přidejte tuto `typedef` na druhý řádek jenom po `#pragma once`:  
  
        ```  
        typedef uint8 byte;  
  
        ```  
  
    2.  Přidat `WebHostHidden` atribut přímo nad začátku `Class1` deklarace.  
  
        ```  
        [Windows::Foundation::Metadata::WebHostHidden]  
        ```  
  
    3.  Přidejte tento podpis veřejnou metodu `Class1`:  
  
        ```  
        Windows::Foundation::IAsyncAction^ Negativize(Windows::UI::Xaml::Media::Imaging::WriteableBitmap^ bm);  
        ```  
  
    4.  Přidání podpisu z `GetPointerToPixelData` metodu, která se zobrazí ve starší fragmentu kódu. Ujistěte se, že tato metoda je privátní.  
  
3.  V Class1.cpp  
  
    1.  Přidejte tyto `#include` direktivy a deklarace oboru názvů:  
  
        ```  
  
        #include <ppltasks.h>  
        #include <wrl.h>  
        #include <robuffer.h>  
  
        using namespace Windows::Storage;  
        using namespace Windows::UI::Xaml::Media::Imaging;  
        using namespace Windows::Storage::Streams;  
        using namespace Microsoft::WRL;  
  
        ```  
  
    2.  Přidat implementaci `GetPointerToPixelData` z předchozích fragmentu kódu.  
  
    3.  Přidat implementaci `Negativize`. Tato metoda vytvoří efekt, který se podobá negativní filmu přehozením hodnotu každé hodnoty RGB v pixelech. Usnadňujeme metodu asynchronní vzhledem k tomu, že na větší Image může trvat postřehnutelné množství času na dokončení.  
  
        ```  
        IAsyncAction^ Class1::Negativize(WriteableBitmap^ bm)  
        {  
            unsigned int length;  
            byte* sourcePixels = GetPointerToPixelData(bm->PixelBuffer, &length);  
            const unsigned int width = bm->PixelWidth;  
            const unsigned int height = bm->PixelHeight;  
  
            return create_async([this, width, height, sourcePixels]  
            {          
                byte* temp = sourcePixels;  
                for(unsigned int k = 0; k < height; k++)  
                {          
                    for (unsigned int i = 0; i < (width * 4); i += 4)  
                    {  
                        int pos = k * (width * 4) + (i);  
                        temp[pos] = ~temp[pos];  
                        temp[pos + 1] = ~temp[pos + 1] / 3;  
                        temp[pos + 2] = ~temp[pos + 2] / 2;  
                        temp[pos + 3] = ~temp[pos + 3];  
                    }  
                }  
            });  
  
        }  
        ```  
  
        > [!NOTE]
        >  Tato metoda může pracovat rychleji, pokud použijete AMP nebo knihovny Ppl pro paralelní zpracování operace.  
  
4.  Zajistěte, aby mít alespoň jeden obrázek do složky Obrázky a stiskněte klávesu F5 ke kompilaci a spuštění programu.