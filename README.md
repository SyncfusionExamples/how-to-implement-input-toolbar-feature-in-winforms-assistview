# How to Implement the Input Toolbar Feature in WinForms AI AssistView

A sample demonstrating how to enable and use the Input Toolbar feature in the Syncfusion WinForms `SfAIAssistView` control. The toolbar exposes quick-action buttons beside the prompt editor so users can attach files, upload images, record audio, and invoke custom actions before sending a prompt.

## Description

This WinForms sample showcases the Input Toolbar capability of Syncfusion's `SfAIAssistView` control. It provides a clean working reference for enabling the toolbar, populating quick-action buttons, responding to user interactions, managing file attachments, and surfacing feedback through toast notifications inside the chat input area.

## Overview

The `SfAIAssistView` control ships with a built-in Input Toolbar that pairs naturally with the Attachments and Toast Notification features. The selected media, status messages, and feedback all appear inside the same input area, providing a fluid chat experience without leaving the prompt editor.

The sample demonstrates how to wire the toolbar into an existing AI chat workflow that is bound to a `ViewModel` through the `Messages` and `ShowTypingIndicator` properties, while allowing the toolbar's quick actions to operate independently throughout the conversation.

## Prerequisites

- Visual Studio with the .NET Framework 4.6.2 targeting pack installed.
- The Syncfusion WinForms `SfAIAssistView` package referenced by `AIAssistView/AssistView_NET462.csproj`.
- The required `using` directives registered where the toolbar is configured.

## Enabling the Input Toolbar

By default the Input Toolbar is hidden from the prompt editor. The sample enables the toolbar by toggling the `IsInputToolbarVisible` property on the `SfAIAssistView` instance, causing the toolbar to render next to the prompt area without affecting the existing layout, data bindings, or underlying chat workflow.

## Input Toolbar Items

The sample populates the `InputToolbarItems` collection with three quick-action buttons covering the most common scenarios. The Attach File button opens a file picker and attaches the chosen file to the prompt, the Upload Image button is reserved for image upload workflows, and the Record Audio button is reserved for voice input workflows. Each `InputToolbarItem` is configured with a unique Name, an informative ToolTip, a glyph or short Text, and an IsVisible flag so buttons can be toggled as needed.

## Responding to Toolbar Clicks

The sample subscribes to the `InputToolbarItemClicked` event to react whenever the user taps one of the toolbar buttons. Based on the clicked item's Name, the application dispatches the corresponding action such as invoking the file attachment workflow or triggering other custom behaviors.

## Action Buttons

In addition to the toolbar buttons, the sample configures an `ActionButtons` collection so a toolbar item can expose a popup of secondary actions. Each entry provides a Name for identification and a Text for display, and the `ActionButtonClicked` event is used to dispatch the picked action back into the application's workflow.

## Attachments

The `Attachments` collection is used as the recommended container for files chosen through the toolbar. The sample builds new `AttachmentItem` instances from the file system, populates properties such as FileName, FileSize, FileIcon, FilePath, and FileExtension, and validates the file size before appending the attachment to the input area.

To keep the input area clean for subsequent prompts, the sample clears the `Attachments` collection inside the `PromptRequest` handler after the user's message has been forwarded to the chat workflow.

## Toast Notifications

The sample uses toast notifications to confirm upload outcomes and surface validation errors. Different notification severities communicate success versus rejection of an uploaded file, giving users immediate feedback for the toolbar actions they perform.

## Helper Utilities

Two helper utilities support the toolbar-driven file workflow. One helper formats file sizes into human-readable labels, while the other extracts the appropriate file icon for the attachment cards. These helpers keep the input area presentation consistent regardless of the file types chosen by the user.

## Running the Sample

Open `AIAssistView/AssistView_NET462.sln` in Visual Studio, restore NuGet packages, and run the project. After configuring the AI credentials through the in-app `AISettingsForm`, start a chat session. The Input Toolbar appears next to the prompt editor with the Attach, Image Upload, and Voice Input quick-action buttons ready for use.

## Topics

winforms syncfusion ai-assistview input-toolbar csharp windows-forms sfaiassistview attachments toast-notifications chatbot conversational-ai