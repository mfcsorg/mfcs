# Model Function Calling Standard (MFCS)
MFCS is an open-standard protocol designed to facilitate interaction between Models and external tools. It defines the format of interaction prompts and the specifications for calling methods.

## Input Prompt Format Specifications
- **Principle Requirements**: Defines the format and method for tool calls, ensuring the Model can correctly parse and return the specified format as needed. It guarantees the parsing module can accurately complete the parsing and imposes constraints on the Model's output.
- **Tool List Information Section**: The Prompt specifically defines a `tool_list` tag, which is the area containing tool list information. This section includes the names, descriptions, and parameters of all available tools.
- **Memory Information Section**: The memory section uses the `memory_list` tag to store long-term memory, character settings, preferences, and other information.
- **Model Output Requirements**: The Prompt also specifies the output format for the Model, primarily to ensure the user can accurately determine whether tool calls or memory queries are needed and correctly parse the required parameters. This ensures no dependency on the Model and allows compatibility with general-purpose models, including those that do not support Function Calling.

For detailed format specifications, refer to [Prompt](https://github.com/mfcsorg/mfcs-prompt/blob/main/ToolPrompt.txt).

## Usage Steps
From the application's perspective, the steps to use MFCS are as follows:

### 1. Obtain the Standard Prompt
Upon receiving user input, the application processes the request using the Model. First, call the MFCS SDK to retrieve the standard Prompt. Combine it with the user's input to form the complete Prompt (in a single contextual conversation, the standard Prompt typically only needs to be obtained once).

### 2. Call the Model
After generating the Prompt in the previous step, input it to the Model for processing. The Model will parse the Prompt's content and generate the corresponding output.

### 3. Parse the Model Output
The Model's output requires parsing. Call the MFCS SDK's Model output parsing interface to parse the output. The result may include parameters and tool names for tool calls or direct results to be output to the user.

### 4. Determine Whether Tool Calls Are Needed
Based on the standardized parsing result, determine whether a tool call is required. If yes, proceed to the next step with the tool name and parameter information. If not, skip to Step 7 to return the result to the user.

### 5. Call the Tool
Match the returned function name to the corresponding function and execute the call.

### 6. Input Tool Results to the Model
Feed the tool's execution results from the previous step into the Model, then proceed to Step 3 with the Model's output for parsing.

### 7. Return Results to the User
Return the results to the user, completing one full interaction (in some cases, intermediate results may be continuously output during the conversation).