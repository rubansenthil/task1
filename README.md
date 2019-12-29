# task1
<?php

interface Builder
{
    
  public function producePartA(): string;

    public function producePartB(): string;

    public function producePartC(): string;
}

class ConcreteBuilder1 implements Builder
{
    private $product;

    public function __construct()
    {
        $this->reset();
    }

    public function reset()
    {
        return $this->product = new Product1;
    }

    
    public function producePartA(): string
    {
        echo 'r'; die;
       return  $this->product->parts[] = "PartA1";
    }

    public function producePartB(): string
    {
        return $this->product->parts[] = "PartB1";
    }

    public function producePartC(): string
    {
       return $this->product->parts[] = "PartC1";
    }
 
    public function getProduct(): Product1
    {
        $result = $this->product;
        $this->reset();

        return $result;
    }
}


class Product1
{
    public $parts = [];

    public function listParts()
    {
        echo "Product parts: " . implode(', ', $this->parts) . "\n\n";
    }
}

class Director
{
   
    private $builder;

  
    public function setBuilder(Builder $builder)
    {
        return $this->builder = $builder;
    }

    
    public function buildMinimalViableProduct(): string
    {
       return $this->builder->producePartA();
    }

    public function buildFullFeaturedProduct(): string
    {
        return $this->builder->producePartA();
        return $this->builder->producePartB();
        return $this->builder->producePartC();
    }
}


function clientCode(Director $director)
{
   
    $builder = new ConcreteBuilder1;
    
    $director->setBuilder($builder);

    echo "Standard basic product:<br/>";
    $director->buildMinimalViableProduct();
