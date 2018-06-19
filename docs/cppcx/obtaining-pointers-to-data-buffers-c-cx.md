---
title: Získání ukazatele na datové vyrovnávací paměti (C + +/ CX) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: db4f9370-dd95-4896-b5b8-4b202284f579
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 42f363cd3af602685890cb8957cf9978c88602a2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090546"
---
# <a name="obtaining-pointers-to-data-buffers-ccx"></a>Získání ukazatele na datové vyrovnávací paměti (C + +/ CX)
V prostředí Windows Runtime [Windows::Storage::Streams::IBuffer](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ibuffer.aspx) rozhraní zajišťuje jazykově neutrální, na základě datového proudu pro přístup k datové vyrovnávací paměti. V jazyce C++ můžete získat nezpracovaná ukazatel základního bajtového pole pomocí rozhraní Windows Runtime knihovny IBufferByteAccess, která je definována v robuffer.h. Pomocí tohoto přístupu můžete upravit bajtové pole na místě bez provedení všechny nepotřebné kopie data.  
  
 Následující diagram znázorňuje obrázek element XAML, jejichž zdrojem je [Windows::UI::Xaml::Media::Imaging WriteableBitmap](http://msdn.microsoft.com/%20library/windows/apps/windows.ui.xaml.media.imaging.writeablebitmap.aspx). Klientskou aplikaci, která je napsána v libovolném jazyce můžete předat odkaz na `WriteableBitmap` do C++ kód a potom C++ můžete použít odkaz na získat na základní vyrovnávací paměti. V aplikaci univerzální platformu Windows, který je napsán v jazyce C++ můžete použít funkci v následujícím příkladu přímo ve zdrojovém kódu bez balení v prostředí Windows Runtime součásti.  
  
 ![C&#43; &#43; kód přímo přístup k datům pixelů](../cppcx/media/ibufferbyteaccessdiagram.png "IBufferByteAccessDiagram")  
  
## <a name="getpointertopixeldata"></a>GetPointerToPixelData  
 Přijímá následující metodu [Windows::Storage::Streams::IBuffer](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.ibuffer.aspx) a vrátí nezpracovaná ukazatel do základního bajtového pole. Pro volání funkce, předejte [WriteableBitmap::PixelBuffer](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.media.imaging.writeablebitmap.pixelbuffer.aspx) vlastnost.  
  
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
 Následující kroky ukazují, jak vytvořit aplikaci C# univerzální platformu Windows, která předá `WriteableBitmap` pro prostředí Windows Runtime C++ součásti knihovny DLL. Kód jazyka C++ získá ukazatel do vyrovnávací paměti pixelů a provádí jednoduchých úprav na místě na bitovou kopii. Alternativně můžete vytvořit klientskou aplikaci v jazyce Visual Basic, JavaScript nebo C++ místo C#. Pokud používáte C++, nepotřebujete komponentu knihovny DLL; Tyto metody můžete přidat pouze přímo na třídě MainPage nebo jiné třídy, které definujete.  
  
#### <a name="create-the-client"></a>Vytvoření klienta  
  
1.  Šablona projektu prázdnou aplikaci použijte k vytvoření aplikace C# univerzální platformu Windows.  
  
2.  V MainPage.xaml  
  
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
  
    1.  Přidejte tyto deklarace oborů názvů:  
  
        ```  
        using Windows.Storage;  
        using Windows.Storage.FileProperties;  
        using Windows.UI.Xaml.Media.Imaging;  
        using Windows.Storage.Streams;  
        using Windows.Storage.Pickers;  
        ```  
  
    2.  Přidat `WriteableBitmap` členské proměnné na `MainPage` třídy a pojmenujte ji `m_bm`.  
  
        ```  
        private WriteableBitmap m_bm;  
        ```  
  
    3.  Použít následující kód k nahrazení `OnNavigatedTo` se zakázaným inzerováním metoda. Nástroje pro výběr souborů otevře při spuštění aplikace. (Všimněte si, že `async` – klíčové slovo se přidá do signatury funkce).  
  
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
  
    4.  Obslužné rutiny události pro klikněte na tlačítko přidáte. (Protože `ImageManipCPP` odkaz na obor názvů nebyl vytvořen, ale může mít vlnovkou v okně editoru.)  
  
        ```  
        async private void Button_Click_1(object sender, RoutedEventArgs e)  
                {  
                    ImageManipCPP.Class1 obj = new ImageManipCPP.Class1();  
                    await obj.Negativize(m_bm);  
                    Pic.Source = m_bm;  
                }  
        ```  
  
#### <a name="create-the-c-component"></a>Vytvoření komponentou C++  
  
1.  Přidat novou součást C++ prostředí Windows Runtime do stávajícího řešení a pojmenujte ji `ImageManipCPP`. Přidat odkaz na jeho v projektu C# kliknutím pravým tlačítkem na takový projekt v **Průzkumníku řešení** a výběr **přidat**, **odkaz**.  
  
2.  V Class1.h  
  
    1.  Přidejte tuto `typedef` na druhém řádku právě po `#pragma once`:  
  
        ```  
        typedef uint8 byte;  
  
        ```  
  
    2.  Přidat `WebHostHidden` atribut nad začátku `Class1` deklarace.  
  
        ```  
        [Windows::Foundation::Metadata::WebHostHidden]  
        ```  
  
    3.  Přidejte tento podpis veřejná metoda k `Class1`:  
  
        ```  
        Windows::Foundation::IAsyncAction^ Negativize(Windows::UI::Xaml::Media::Imaging::WriteableBitmap^ bm);  
        ```  
  
    4.  Přidat podpis z `GetPointerToPixelData` metoda, která se zobrazí ve starší fragmentu kódu. Ujistěte se, že tato metoda je soukromé.  
  
3.  V Class1.cpp  
  
    1.  Přidat tyto `#include` direktivy a deklarace oborů názvů:  
  
        ```  
  
        #include <ppltasks.h>  
        #include <wrl.h>  
        #include <robuffer.h>  
  
        using namespace Windows::Storage;  
        using namespace Windows::UI::Xaml::Media::Imaging;  
        using namespace Windows::Storage::Streams;  
        using namespace Microsoft::WRL;  
  
        ```  
  
    2.  Přidání implementace `GetPointerToPixelData` z dřívějších fragmentu kódu.  
  
    3.  Přidání implementace `Negativize`. Tato metoda vytváří efekt podobná záporné filmu podle Prohodit hodnota každé hodnoty RGB v pixelech. Můžeme provádět metodu asynchronní protože větší Image může trvat znatelné množství času na dokončení.  
  
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
        >  Tato metoda může pracovat rychleji, pokud používáte AMP nebo Parallel Library vzory učinit paralelní operaci.  
  
4.  Zajistěte, aby mít alespoň jeden obrázek do složky Obrázky a potom stiskněte klávesu F5, aby zkompilování a spuštění programu.