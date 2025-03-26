# VGEN_Testing
This repo stores the test result of LLM (temporarily GPT-4o) on VGEN. The test is done by using Github Copilot Chat and the results are stored in a markdown file. The test is done by using the following steps:
1. **Test the LLM**: The LLM is tested by using the test cases provided in the [VGEN-Verilog for LLM](https://github.com/shailja-thakur/VGen).
2. **Store the results**: The results are stored in a markdown file in this repo.
3. **Hint Level**: There are multiple prompt options of various clarity in a testcase. I roughly selected the most suitable one. Namely the spec should be clear and concise for me to understand each I/O, but no extra information on the implementation. (hint level category TBD)
## Takeaways
- The LLM is able to understand the test cases and generate the expected output as these test cases are simple and straightforward for any trained EE student.
- The LLM might [generate redundant logic](https://github.com/yt-tony-liu/VGEN_Testing/vgen_intermediate_4.md#comment) in the code. EDA tools could easily optimize it, but it could be a problem for larger designs.
- Some syntax errors i.e. unwanted latches. 