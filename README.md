# CEAM-Task-Phase-CV

I made a small CNN with 3 objects: pen, sharpener, and eraser, for which I took about 20 photos for each object in different orientation and backgrounds.

To understand stuff, I did 6 experiments,
1. **Baseline**: Adam optimizer, Batch Size 16, Dropout 0.5, Learning Rate 0.001
2. **High Learning Rate**: Changed learning rate to 0.1
3. **Low Learning Rate**: Changed learning rate to 0.00001
4. **No Dropout**: Set dropout to 0.0 (removed regularization)
5. **SGD**: Changed the optimizer from Adam to SGD
6. **Small Batch**: Changed batch size from 16 to 2

## Observations
- **Baseline**: Learned reasonably well
- **Low Learning Rate**: Learned way too slowly.
- **No Dropout**: Trained well on the training data, but it was not as smooth.
- **SGD**: Trained much slower than Adam.
- **Small Batch**: The loss curve was very rigid kind of.

## What Failed
The **High Learning Rate** experiment failed. The loss curve just bounced around randomly and the accuracy was like near 33% (which is basically like random guessing for a 3-class problem). 
I found this is called "gradient instability". The step size for the optimizer was so huge that it kept overshooting the correct solution and never settled.

## Insights
I learned that hyperparameter tuning is a delicate balance. You can't just bring up the learning rate to learn faster because it breaks the training completely. I also learned that batch sizes impact how "smooth" your learning curve looks, and that Adam is generally a much safer bet than SGD for getting fast results.
