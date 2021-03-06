---
title: "Editor Imports | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editors [Visual Studio SDK], new - services"
ms.assetid: 8d096de3-33b4-427a-a122-4aeff8a72da0
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
translation.priority.mt: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# Editor Imports
You can import a number of editor services, factories, and brokers that provide your extension with different kinds of access to the core editor. For example, you can import the <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> to provide you with a <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> for a given content type. (This navigator allows you perform different kinds of searches on a text buffer.)  
  
 To use an editor import, you import it as a field or property of a class that exports a Managed Extensibility Framework component part.  
  
> [!NOTE]
>  For more information about the Managed Extensibility Framework, see [Managed Extensibility Framework (MEF)](/dotnet/framework/mef/index).  
  
## Import Syntax  
 The following example shows how to import the editor options factory service.  
  
```  
[Import]  
internal IEditorOptionsFactoryService EditorOptions { get; set; }  
```  
  
 If you want to import the service as a field and not a property, you should set it to `null` in the declaration in order to avoid the compiler warnings about not assigning to a variable:  
  
```  
[Import]  
internal IEditorOptionsFactoryService m_editorOptions = null;  
```  
  
 For more examples of using imports, see the following walkthroughs:  
  
 [Walkthrough: Creating a Margin Glyph](../extensibility/walkthrough-creating-a-margin-glyph.md)  
  
 [Walkthrough: Customizing the Text View](../extensibility/walkthrough-customizing-the-text-view.md)  
  
 [Walkthrough: Highlighting Text](../extensibility/walkthrough-highlighting-text.md)  
  
 [Walkthrough: Displaying QuickInfo Tooltips](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)  
  
 [Walkthrough: Displaying Signature Help](../extensibility/walkthrough-displaying-signature-help.md)  
  
 [Walkthrough: Displaying Statement Completion](../extensibility/walkthrough-displaying-statement-completion.md)  
  
 [Walkthrough: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)  
  
## Importing the Service Provider  
 You can also import a <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> (found in the assembly Microsoft.VisualStudio.Shell.Immutable.10.0) in the same way to get access to Visual Studio services:  
  
```  
[Import]  
internal SVsServiceProvider ServiceProvider = null;   
```  
  
 See [Walkthrough: Accessing the DTE Object from an Editor Extension](../extensibility/walkthrough-accessing-the-dte-object-from-an-editor-extension.md) for more information.  
  
## Services  
 Editor services are generally single entities that provide a service and are shared across multiple components.  
  
|Import|Provides|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Utilities.IFileExtensionRegistryService>|The relationship between file extensions and <xref:Microsoft.VisualStudio.Utilities.IContentType> objects.|  
|<xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>|The collection of <xref:Microsoft.VisualStudio.Utilities.IContentType> objects.|  
|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformationService>|<xref:Microsoft.VisualStudio.Editor.IVsFontsAndColorsInformation> objects|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>|Many editor adapter objects:<br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator><br /><br /> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|  
|<xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearchFactoryService>|An <xref:Microsoft.VisualStudio.Text.IncrementalSearch.IIncrementalSearch> object for a given text view.|  
|<xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.ITextDocumentFactoryService>|An <xref:Microsoft.VisualStudio.Text.ITextDocument>.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceService>|An <xref:Microsoft.VisualStudio.Text.Differencing.IDifferenceCollection%601> of differences.|  
|<xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalStringDifferenceService>|An <xref:Microsoft.VisualStudio.Text.Differencing.IHierarchicalDifferenceCollection> of differences.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>|An <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> or an <xref:Microsoft.VisualStudio.Text.Projection.IElisionBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>|An <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> for a set of <xref:Microsoft.VisualStudio.Text.ITextBuffer> objects.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>|An <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> for a <xref:Microsoft.VisualStudio.Text.ITextBuffer>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IViewClassifierAggregatorService>|An <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> for a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMapService>|An <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> for a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>|An <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap> for a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Classification.IClassificationTypeRegistryService>|Maintains the collection of <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objects.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IBufferTagAggregatorFactoryService>|An <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> for a text buffer.|  
|<xref:Microsoft.VisualStudio.Text.Tagging.IViewTagAggregatorFactoryService>|An <xref:Microsoft.VisualStudio.Text.Tagging.ITagAggregator%601> for a text view.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IEditorOptionsFactoryService>|The <xref:Microsoft.VisualStudio.Text.Editor.IEditorOptions> for the specified scope.|  
|<xref:Microsoft.VisualStudio.Text.Editor.IScrollMapFactoryService>|An <xref:Microsoft.VisualStudio.Text.Editor.IScrollMap> for a text view.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|An <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndent> for a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentationService>|Gets the automatic indentation through the <xref:Microsoft.VisualStudio.Text.Editor.ISmartIndentProvider> objects.|  
|<xref:Microsoft.VisualStudio.Text.Editor.ITextEditorFactoryService>|Manages the <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> for a <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IFormattedTextSourceFactoryService>|An <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.IRtfBuilderService>|Generates RTF-formatted text from a set of snapshot spans.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencerFactoryService>|An <xref:Microsoft.VisualStudio.Text.Formatting.ITextAndAdornmentSequencer> for an <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Formatting.ITextParagraphPropertiesFactoryService>|A <xref:System.Windows.Media.TextFormatting.TextParagraphProperties> for formatting text lines in a view.|  
|<xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService>|A <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperations> object for an <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextSearchService>|Searches a text snapshot.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>|An <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator> for an <xref:Microsoft.VisualStudio.Text.ITextBuffer> by <xref:Microsoft.VisualStudio.Utilities.IContentType>.|  
|<xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService>|An <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> for a text view.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IGlyphService>|A standard set of glyphs.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStackMapService>|An <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSessionStack> for a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IWpfKeyboardTrackingService>|Tracks keyboard handling.|  
|<xref:Microsoft.VisualStudio.Language.StandardClassification.IStandardClassificationService>|Standard <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> objects.|  
|<xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistoryRegistry>|Maintains the relationship between text buffers and  <xref:Microsoft.VisualStudio.Text.Operations.ITextUndoHistory> objects.|  
  
## Other Imports  
 Provider factories and brokers are generally entities that can have multiple instances in multiple components.  
  
|Import|Provides|  
|------------|--------------|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IErrorProviderFactory>|A <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> of type <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>) for the given buffer.|  
|<xref:Microsoft.VisualStudio.Text.Adornments.ITextMarkerProviderFactory>|A text marker tagger (a <xref:Microsoft.VisualStudio.Text.Tagging.SimpleTagger%601> of type <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>).|  
|<xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProviderFactory>|An <xref:Microsoft.VisualStudio.Text.Adornments.IToolTipProvider> for a given <xref:Microsoft.VisualStudio.Text.Editor.ITextView>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSession>.|  
|<xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>|An <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSession>.|  
  
## See Also  
 [Language Service and Editor Extension Points](../extensibility/language-service-and-editor-extension-points.md)