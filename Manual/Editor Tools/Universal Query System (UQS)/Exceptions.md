# Exceptions

- Source: https://www.cryengine.com/docs/static/engines/cryengine-5/categories/23756816/pages/29450498
- Page ID: 29450498
- Breadcrumb: Editor Tools > Universal Query System (UQS) > Exceptions
- Parent: Universal Query System (UQS)

## Content

## Overview

The Universal Query System (UQS) supports the concept of "managed exceptions". These are similar to C++ exceptions, but are restricted to specific places and don't make use of the 'throw' keyword of the C++ programming language. Just like in C++, exceptions in the UQS are meant for the programmer to clearly bail out and notify that, for example, some parameters of the query had bad values that could no longer be dealt with in a safe way.

### Details

Exceptions can occur in:

- Generators
- InstantEvaluators
- DeferredEvaluators
- Functions

Depending on where exceptions occur, then different effects will happen:

Occurrence | Effect
--- | ---
**Generator** | The whole query bails out with an exception.
**InstantEvaluator** | Only the current item will be discarded (marked as having encountered an exception).
**DeferredEvaluator** | Only the current item will be discarded (marked as having encountered an exception).
**Function** | The function will stop calling further child functions and propagate the exception up to the caller (i. e. Generator or Evaluator) from where it gets handled.

### Example

Say, you have an evaluator that is supposed to score the distance between 2 points. A potential issue that we need to guard against could be an unexpected division by zero:

```
UQS::Client::IInstantEvaluator::ERunStatus CInstantEvaluator_ScoreDistance::DoRun(const SRunContext& runContext, const SParams& params) const
{
// guard against potential div-by-zero and other weird behavior
if (params.distanceThreshold <= 0.0f)
{
runContext.error.Format("param 'distanceThreshold' should be > 0.0 (but is: %f)", params.distanceThreshold);
return uqs::client::IInstantEvaluator::ERunStatus::ExceptionOccurred;
}

const float distanceBetweenPoints = (params.pos1 - params.pos2).GetLength();
runContext.evaluationResult.score = std::min(distanceBetweenPoints, params.distanceThreshold) / params.distanceThreshold;

return UQS::Client::IInstantEvaluator::ERunStatus::Finished;
}
```
