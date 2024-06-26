# This repository contains code for the paper titled "Improving Planning with Large Language Models: A Brain-inspired Agentic Architecture"

## Requirements
- python 3.9.17
- numpy==1.24.3
- tqdm==4.65.0
- json==2.0.9
- openai==1.24.1

## Tower of Hanoi (ToH)


For ToH task, the codebase (inside `toh` directory) contains files to run LLM-PFC and GPT-4 baselines such as zero-shot, in-context learning (ICL), chain-of-thought (CoT ICL), multi-agent debate (MAD), and tree of thought (ToT). It also contains files to evaluate the outputs generated by the model runs.  

To run the above models you need to specify two required arguments- 1) openAI API key 2) directory name where output log files will be stored

For example to run and evaluate LLM-PFC first execute, `python gpt4_llmpfc_toh.py --openai_api_key '<YOUR OPENAI KEY>' --output_dir '<OUTPUT DIRECTORY NAME>'`

Then execute, `python gpt4_llmpfc_toh_eval.py --output_dir '<OUTPUT DIRECTORY NAME>'`



To run and evaluate one of the baseline models, for example, GPT-4 ICL first execute, `python gpt4_icl_toh.py --openai_api_key '<YOUR OPENAI KEY>' --output_dir '<OUTPUT DIRECTORY NAME>'`

Then execute, `python gpt4_icl_toh_eval.py --output_dir '<OUTPUT DIRECTORY NAME>'`

## Cogeval

For the Cogeval tasks (Valuepath, Steppath, Reward Revaluation, and Detour), the codebase (inside `cogeval` directory) contains files to run LLM-PFC and GPT-4 baselines such as zero-shot, in-context learning (ICL), chain-of-thought (CoT ICL), multi-agent debate (MAD), and tree of thought (ToT). It also contains files to evaluate the outputs generated by the model runs.  

To run the above models you need to specify two required arguments- 1) openAI API key 2) directory name where output log files will be stored

For example to run and evaluate LLM-PFC on the Valuepath task first execute, `python gpt4_llmpfc_valuepath.py --openai_api_key '<YOUR OPENAI KEY>' --output_dir '<OUTPUT DIRECTORY NAME>'`

Then execute, `python gpt4_llmpfc_valuepath_eval.py --output_dir '<OUTPUT DIRECTORY NAME>'`


To run and evaluate one of the baseline models, for example, GPT-4 ICL on the Valuepath task first execute, `python gpt4_standard_icl_valuepath.py --openai_api_key '<YOUR OPENAI KEY>' --output_dir '<OUTPUT DIRECTORY NAME>'`

Then execute, `python gpt4_valuepath_baselines_eval.py --output_dir '<OUTPUT DIRECTORY NAME>'`



## Planbench

For the mystery blocksworld task, the codebase (inside `planbench/mystery_blocksworld` directory) contains files to run LLM-PFC and GPT-4 baselines such as zero-shot, in-context learning (ICL), chain-of-thought (CoT ICL), and multi-agent debate (MAD). It also contains files to generate plan responses JSON for further evaluation.  

First clone the LLMs-Planning repo, inside `planbench/mystery_blocksworld` directory from https://github.com/karthikv792/LLMs-Planning, and the follow the instructions given in https://github.com/karthikv792/LLMs-Planning/tree/main/plan-bench for setup.

To run the above models you need to insert the following block of code at the start of the script after the import statements. Fill in the `api_key`, `azure_endpoint`, and `deployment_name`. Also as a required argument specify the directory name where output log files will be stored
```
client = AzureOpenAI(
	api_key="",
	api_version="2024-02-01",
	azure_endpoint=""
	)
deployment_name = ''
```
For example to run LLM-PFC first execute, `python gpt4_llmpfc_mystery_blocksworld_plan_generation.py --output_dir '<OUTPUT DIRECTORY NAME>'`

Then to generate the plan response JSON execute, `python gpt4_llmpfc_genplan_response_json.py --output_dir '<OUTPUT DIRECTORY NAME>'`

Finally, to evaluate the plan response JSON execute, `python LLMs-Planning/plan-bench/response_evaluation.py --task 't1' --config 'mystery_blocksworld' --engine 'llmpfc' --ignore_existing --verbose 'True'`


To run one of the baseline models, for example, GPT-4 ICL first execute, `python gpt4_mystery_blockworld_plan_generation_icl.py --output_dir '<OUTPUT DIRECTORY NAME>'`

Then to generate the plan response JSON execute, `python gpt4_baselines_genplan_response_json.py --output_dir '<OUTPUT DIRECTORY NAME>' --model 'gpt4_icl'`

Finally, to evaluate the plan response JSON execute, `python LLMs-Planning/plan-bench/response_evaluation.py --task 't1' --config 'mystery_blocksworld' --engine 'gpt4_icl' --ignore_existing --verbose 'True'`

## StrategyQA
For the strategyQA task, the codebase (inside `strategyQA` directory) contains files to run LLM-PFC and GPT-4 baselines such as chain-of-thought (CoT), and tree of thought (ToT).  

To run the above models you need to insert the following block of code at the start of the script after the import statements. Fill in the `api_key`, `azure_endpoint`, and `deployment_name`.
```
client = AzureOpenAI(
	api_key="",
	api_version="2024-02-01",
	azure_endpoint=""
	)
deployment_name = ''
```
For example to run LLM-PFC execute, `python llmpfc_strategyqa.py`

